# Workflow State

Workflow state is the canonical source of task progress.

## Schema

```yaml
workflow:
  id: TASK-001
  title: "<task title>"
  classification: complex
  state: SPEC_READY

  artifacts:
    spec: SPEC-001
    plan: null
    verification: null
    research: null

  blockers: []

  next_action: create implementation plan
```

Omit artifact fields that do not apply when practical.

---

## Classification Values

Allowed values:

- trivial
- simple
- complex
- exploratory

---

## State Values

Allowed values:

- INTAKE
- RESEARCHING
- SPEC_DRAFT
- SPEC_READY
- PLAN_DRAFT
- PLAN_READY
- EXECUTING
- VERIFYING
- BLOCKED
- DONE

Do not invent additional state names.

---

## State Transitions

Normal complex workflow:

INTAKE
→ SPEC_DRAFT
→ SPEC_READY
→ PLAN_DRAFT
→ PLAN_READY
→ EXECUTING
→ VERIFYING
→ DONE

Exploratory workflow:

INTAKE
→ RESEARCHING
→ SPEC_DRAFT
→ SPEC_READY
→ PLAN_DRAFT
→ PLAN_READY
→ EXECUTING
→ VERIFYING
→ DONE

---

## Return Transitions

Implementation defect:

VERIFYING
→ EXECUTING

Implementation strategy invalid:

EXECUTING or VERIFYING
→ PLAN_DRAFT

Requirement or scope change:

PLAN_DRAFT, EXECUTING, or VERIFYING
→ SPEC_DRAFT

---

## Blocking

Use `BLOCKED` only when progress cannot continue without external information, access, dependency, or material decision.

When blocked, record:

```yaml
state: BLOCKED
blocked_from: PLAN_DRAFT

blockers:
  - "<specific blocker>"

next_action: "<action required to unblock>"
```

After resolution, return to `blocked_from` or the appropriate resulting state.

---

## Status Reporting

When asked to check status, report:

Task
State
Completed artifacts
Current blocker, if any
Next action

Example:

Task: TASK-001  
State: PLAN_READY

Spec: SPEC-001 ready  
Plan: PLAN-001 ready  
Verification: not started

Blockers: none

Next: execute P-01

## Persistence and Consistency

For persisted tasks save `workflow-state.yaml` and `spec.md`, `plan.md`, `verification.md`, and optional `research.md` in one task directory. Artifact IDs resolve to those filenames within that directory; IDs are scoped to the task. Choose a non-colliding task directory and ID. `version: 1` denotes the schema version, not the artifact revision.

Required workflow keys: `id`, `title`, `classification`, `state`, `artifacts`, `blockers`, `next_action`. Uncreated artifacts may be null; omitted artifacts must be inapplicable. `blocked_from` is required only in BLOCKED. Clear it and resolved blockers on resumption. In DONE, use `next_action: null`.

Workflow state is the sole progress source. Artifact `status` only expresses document readiness or assessment completion; a complete Verification may request fixes, and complete Research may report a blocker. Update artifacts first, then state at each transition and before handoff.

Trivial/simple: INTAKE → EXECUTING → VERIFYING → DONE; inspection occurs in INTAKE. Verify directly against the requested outcome with concrete evidence. The full Spec/Plan/Verification contracts apply to complex/exploratory tasks.

Any active stage can enter BLOCKED. Newly discovered prerequisite uncertainty can return active work to RESEARCHING. Material Spec changes from any later stage return to SPEC_DRAFT; strategy changes from PLAN_READY, EXECUTING, or VERIFYING return to PLAN_DRAFT. Reopened DONE work must reassess the appropriate stage.

On Spec changes, mark the Spec and existing Plan draft and invalidate current Verification by setting it in_progress and removing its final decision. On Plan changes, mark Plan draft and invalidate Verification. After implementation fixes, invalidate affected evidence and rerun affected checks before claiming DONE. Preserve unchanged item IDs; do not recycle retired IDs for unrelated requirements. Old evidence remains historical and cannot prove changed behavior.
