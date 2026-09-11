# Research Contract

Research resolves a bounded decision that prevents a reliable Spec. It is not a
general background report.

## Frontmatter

```yaml
---
type: research
version: 1
id: RESEARCH-001
task: TASK-001
status: in_progress
---
```

Allowed `status`: `in_progress`, `complete`.

## Required content

### Question

State the decision that must be made and the criteria that matter.

### Findings

Record decision-relevant findings. Identify the source, code location, command,
experiment, or other evidence for consequential claims; label assumptions.

### Decision

State the selected option and rationale, or the concrete external blocker that
prevents a decision.

### Spec impact

State the requirements, constraints, or acceptance criteria the Spec must add
or change. Reference existing IDs when a Spec already exists.

Add options, detailed evidence, or remaining unknowns only when they materially
support the decision.

## Completion

Set `status: complete` when the question is answered well enough to write the
Spec, or when a concrete blocker is evidenced. Any remaining unknown must be
immaterial to the contract or named as the blocker. Feed the decision into the
Spec; Research does not replace it.
