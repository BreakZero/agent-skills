# Spec Contract

The Spec defines the observable outcome. Include implementation details only
when they are fixed constraints.

## Frontmatter

```yaml
---
type: spec
version: 1
id: SPEC-001
task: TASK-001
status: draft
---
```

Allowed `status`: `draft`, `ready`.

## Required content

### Goal

State the user-visible or system outcome.

### Scope

Define what must be delivered. Add out-of-scope exclusions only when they
prevent a likely ambiguity.

### Requirements

Give each testable obligation a stable ID:

```text
FR-01: <subject> must <observable behavior> [when <condition>].
NFR-01: <subject> must meet <measurable property>.
```

Use `NFR-*` only for relevant non-functional properties. Record fixed
implementation or compatibility limits as `C-*` constraints when traceability
is useful.

### Acceptance criteria

Define the evidence-bearing result for every requirement and material
constraint:

```text
AC-01 (FR-01): <objectively verifiable result>.
AC-02 (NFR-01, C-01): <objectively verifiable result>.
```

Use Given/When/Then when it improves behavioral clarity. A direct assertion is
better for a simple check.

## Optional content

Add context, constraints, behavior rules, edge cases, assumptions, or open
questions only when they change implementation or verification decisions.

## Ready criterion

Set `status: ready` when:

- the goal and scope are bounded;
- each requirement is testable;
- every material constraint is captured;
- every `FR-*`, `NFR-*`, and material `C-*` is covered by at least one `AC-*`;
- every acceptance criterion references valid IDs and has an objective check;
- no open question could materially change the contract.

A documented assumption may resolve minor ambiguity when it does not change the
user-visible outcome or coverage set.

## Revisions

When the contract changes, return the Spec to `draft` and invalidate affected
Plan and Verification content. Preserve unchanged IDs; retire rather than reuse
an ID whose meaning changed.
