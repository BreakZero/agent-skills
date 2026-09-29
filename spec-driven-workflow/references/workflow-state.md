# Workflow state

Persist a small state record when work must survive handoff, interruption, or audit. Conversation context is sufficient for short continuous work.

Record the task ID, current stage, artifact locations, completed work with evidence needed to resume, concrete blockers, and next action. Use a format that fits the project; for example:

```yaml
id: TASK-001
stage: executing
artifacts:
  spec: spec.md
  plan: plan.md
completed: []
blockers: []
next_action: implement the next planned unit
```

Update the relevant artifact before changing state. Link only artifacts that exist. When scope or strategy changes, remove or mark stale only the completion and verification evidence affected by the revision.

Mark work blocked when no useful authorized step can continue without external information, access, or a decision. Record the needed action and resume at the appropriate stage after it arrives. Mark work done only after the requested outcome meets its current acceptance criteria.
