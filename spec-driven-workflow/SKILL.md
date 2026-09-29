---
name: spec-driven-workflow
description: Structure implementation when architecture, API, data, migration, or security decisions need an explicit contract and acceptance evidence. Skip routine local edits.
---

# Spec-Driven Workflow

Establish what must be true, choose how to achieve it, implement, then verify the outcome. Scale the record to the task: a short conversation can hold a simple contract; use persisted artifacts when the work needs handoff, recovery, auditability, or the user requests them. Do not turn a planning aid into an extra approval gate.

For a local change with a clear outcome, inspect what is relevant, edit, and verify. For work with interacting requirements or material consequences, state the scope, constraints, and observable acceptance criteria before choosing an implementation. Research only a bounded question that prevents a sound decision. If the user requests only research or a plan, deliver that scope.

Continue through the requested outcome. Revise the plan when the implementation path changes; revise the contract when the intended outcome changes. Recheck evidence affected by those revisions. Treat an external dependency as a blocker after completing useful authorized work.

Read a contract below only when creating or updating that artifact:

- [Research](references/research-schema.md): a decision that blocks the contract.
- [Spec](references/spec-schema.md): requirements and acceptance criteria.
- [Plan](references/plan-schema.md): implementation decisions and coverage.
- [Verification](references/verification-schema.md): results against current criteria.
- [Workflow state](references/workflow-state.md): resumable or auditable progress.

Store requested or needed artifacts in the project's preferred location; otherwise use `work/spec-driven-workflow/<task-id>/` in the authorized workspace. Keep stable IDs across revisions and invalidate only evidence affected by a change. Finish when the requested outcome is implemented and sufficiently verified, or report a concrete unresolved blocker.
