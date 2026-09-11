# Workflow State

Use persisted state when work must survive a handoff, interruption, or audit.
For short continuous work, conversation context and normal task tracking are
sufficient.

## Schema

```yaml
workflow:
  version: 2
  id: TASK-001
  title: "<task title>"
  classification: complex
  state: PLAN_READY
  artifacts:
    research: null
    spec: SPEC-001
    plan: PLAN-001
    verification: null
  execution:
    current_step: P-01
    completed_steps: []
    step_evidence: {}
  blockers: []
  next_action: execute P-01
```

Required keys are `version`, `id`, `title`, `classification`, `state`,
`artifacts`, `blockers`, and `next_action`. Add `execution` when a Plan exists.

Allowed classifications: `trivial`, `simple`, `complex`, `exploratory`.

Allowed states:

```text
INTAKE  RESEARCHING  SPEC_DRAFT  SPEC_READY  PLAN_DRAFT  PLAN_READY
EXECUTING  VERIFYING  BLOCKED  DONE
```

Do not copy requirements or Step actions into state. Resolve them from the Spec
and Plan.

## Transitions

Use only the stages required by the selected route:

```text
trivial/simple: INTAKE → EXECUTING → VERIFYING → DONE
complex:        INTAKE → SPEC_DRAFT → SPEC_READY → PLAN_DRAFT → PLAN_READY
                → EXECUTING → VERIFYING → DONE
exploratory:    INTAKE → RESEARCHING → SPEC_DRAFT → ... → DONE
```

Return to `EXECUTING` for an implementation fix, `PLAN_DRAFT` for a strategy
change, and `SPEC_DRAFT` for a contract change. Invalidate only the downstream
Steps and evidence affected by the change.

## Execution progress

`current_step` is the next or active `P-*` Step. Add a Step to
`completed_steps` only after its `Done when` condition passes, and record enough
evidence in `step_evidence` to resume or audit the work. Independent Steps may
run in parallel when their dependencies, targets, and side effects do not
conflict.

Set `current_step: null` when no Step is active. Move to `VERIFYING` when every
required Step is complete.

## Blocking

Use `BLOCKED` only when no useful in-scope work can continue without external
information, access, dependency, or a material decision. Record:

```yaml
state: BLOCKED
blocked_from: EXECUTING
blockers:
  - "<specific blocker>"
next_action: "<external action needed to resume>"
```

Retain the active Step when blocked during execution. After resolution, clear
the blocker and return to the appropriate stage. A failed check is not a blocker
when it can be fixed or re-planned within the existing authorization.

## Persistence

Store `workflow-state.yaml` with its referenced `research.md`, `spec.md`,
`plan.md`, and `verification.md` files. Uncreated or inapplicable artifacts may
be `null`. Update an artifact before updating state to reference its new status,
and ensure every non-null ID resolves to a file with the matching ID.

Workflow state is the source of truth for status reports. Preserve stable IDs
across revisions and remove completion/evidence entries invalidated by changed
meaning. Use `next_action: null` only for `DONE`.
