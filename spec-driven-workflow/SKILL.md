---
name: spec-driven-workflow
description: >
  Structure implementation work when correctness depends on explicit scope,
  requirements, implementation choices, or acceptance evidence. Use for
  architecture, API or data-model changes, migrations, security-sensitive work,
  and other changes with material uncertainty; skip routine local edits.
---

# Spec-Driven Workflow

Define the outcome before choosing the implementation. Use only the artifacts
that reduce material ambiguity or make the work verifiable.

- The **Spec** defines what must be true.
- The **Plan** defines how to make it true.
- **Verification** records the evidence that it is true.

## Route the task

Read [task-classification.md](references/task-classification.md), then choose the
lightest route that preserves correctness:

```text
trivial:      execute → verify
simple:       inspect → execute → verify
complex:      spec → plan → execute → verify
exploratory:  research → spec → plan → execute → verify
```

Classification is a decision aid, not a deliverable. Keep trivial and simple
work in the conversation unless the user requests persistent or auditable artifacts. When
the user requests only research, a Spec, or a Plan, stop after that deliverable
unless implementation is also requested.

## Work by contracts

Read only the reference needed for the current stage:

- **Research:** [research-schema.md](references/research-schema.md) — resolve a
  decision that blocks a reliable Spec.
- **Spec:** [spec-schema.md](references/spec-schema.md) — state the bounded goal,
  requirements, constraints, and objective acceptance criteria.
- **Plan:** [plan-schema.md](references/plan-schema.md) — select an executable
  implementation strategy that traces to the ready Spec.
- **Verification:** [verification-schema.md](references/verification-schema.md)
  — evaluate every current acceptance criterion with fresh evidence.
- **Persistence:** [workflow-state.md](references/workflow-state.md) — use for
  resumable, handed-off, or auditable work; omit for short continuous tasks.

Each stage ends when its reference's completion criterion passes. If it does
not, resolve the uncertainty at the earliest affected stage rather than passing
it downstream.

## Adapt while executing

- Continue for implementation-detail changes that preserve the Spec and Plan.
- Re-plan when the implementation strategy, ordering, targets, or validation
  path is no longer sound.
- Revise the Spec when intended behavior, scope, requirements, constraints, or
  acceptance criteria change.
- Treat missing external information, access, or decisions as blockers only
  after completing all useful work that remains authorized.

Use validation proportional to the change and its risk. Run the checks needed
to establish the acceptance criteria; broaden or repeat them only when failures,
new changes, or unresolved concerns justify it.

Finish when the requested outcome satisfies every applicable acceptance
criterion with sufficient evidence and no material blocker remains. Never
weaken the contract to match the implementation.

## Store artifacts

Keep generated task artifacts outside the installed skill. Follow project
conventions; otherwise use `work/spec-driven-workflow/<task-id>/` in the
authorized workspace. Preserve stable IDs across revisions and invalidate
affected downstream evidence when the Spec or Plan changes. Write prose in the
user's language while keeping schema keys and enums exact.
