# Research Contract

Research is optional.

Use Research only when uncertainty prevents creation of a reliable Spec.

Research exists to resolve decisions, not to accumulate information.

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

Allowed `status` values:

- in_progress
- complete

---

## Required Sections

# Research: <Title>

## Question

State the specific uncertainty that must be resolved.

## Findings

Record only findings relevant to the decision.

## Decision

State the selected conclusion or identify why no conclusion can yet be made.

## Spec Impact

Describe how the result changes or informs the Spec.

Examples:

- Add constraint C-02.
- Define FR-03.
- Resolve streaming architecture.
- No Spec change required.

---

## Conditional Sections

### Options

Use when multiple viable approaches were compared.

Recommended format:

| Option | Advantages | Trade-offs |
|---|---|---|

### Evidence

Include sources, experiments, benchmarks, or code inspection when they materially support the decision.

### Remaining Unknowns

Include only unresolved unknowns that still matter.

---

## Completion Rule

Research may transition to `complete` when it either:

1. resolves the question sufficiently for Spec creation, or
2. identifies a concrete blocker that prevents further progress.

Research must feed into Spec.

Do not transition directly from Research to Plan.

All shown frontmatter fields are required. Support consequential factual findings with source references or actual observations; distinguish assumptions from evidence. A completed report that identifies a blocker puts the workflow in BLOCKED, not SPEC_READY. Research completion alone never authorizes broader implementation.
