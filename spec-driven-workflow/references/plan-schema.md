# Plan Contract

The Plan defines how a ready Spec will be implemented.

A Plan must not redefine requirements.

Input must be a ready Spec.

## Frontmatter

```yaml
---
type: plan
version: 1
id: PLAN-001
task: TASK-001
spec: SPEC-001
status: draft
---
```

Allowed `status` values:

- draft
- ready

---

## Required Sections

# Implementation Plan: <Title>

## Objective

Reference the Spec and state the implementation objective in one or two sentences.

Do not restate the complete Spec.

## Strategy

Describe the overall implementation approach and major design decisions.

## Impacted Areas

Identify expected areas of change.

Recommended format:

| Area | Impact | Notes |
|---|---|---|
| API | Modify | Add relay endpoint |
| Service | Add | Provider relay service |
| Persistence | None | No data storage changes |

## Implementation Steps

Every step must have a stable ID.

```markdown
### P-01 — <Action-oriented title>

**Targets**
- `path/or/module`

**Changes**
- ...

**Covers**
- FR-01
- AC-01

**Validation**
- ...
```

Each step must represent a meaningful, verifiable implementation unit.

Avoid vague steps such as:

`P-01 — Implement backend`

Prefer:

`P-01 — Add relay service`

`P-02 — Expose streaming endpoint`

`P-03 — Add provider error mapping`

---

## Validation

Define the expected validation mechanisms.

Include only applicable categories:

### Build

- command or build condition

### Automated Tests

- unit tests
- integration tests
- existing regression tests

### Manual Verification

- user flow
- API request
- runtime behavior

---

## Traceability

Every functional and non-functional requirement must be covered.

Every Acceptance Criterion must have a planned verification path.

Recommended format:

| Spec Item | Plan Step | Verification |
|---|---|---|
| FR-01 | P-01, P-02 | integration test |
| FR-02 | P-02 | streaming API test |
| AC-01 | P-02 | integration test |
| AC-02 | P-02 | streaming request |

---

## Conditional Sections

Include only when relevant.

### Dependencies

Internal or external dependencies and ordering constraints.

### Risks

Only material implementation risks.

Recommended format:

| Risk | Impact | Mitigation |
|---|---|---|

### Migration / Compatibility

Use when the task affects:

- stored data
- API compatibility
- configuration
- deployment
- backward compatibility

### Rollback

Use only when rollback requires explicit handling.

---

## Plan Readiness Rules

A Plan may transition to `ready` only when:

1. It references a ready Spec.
2. All in-scope requirements are covered.
3. Every Acceptance Criterion has a verification path.
4. Impacted areas are identified.
5. Implementation order is executable.
6. Validation is defined.
7. No Plan step depends on an unresolved Spec decision.

---

## Replanning Rule

Return to Plan without changing Spec when:

- implementation approach changes
- module or file selection changes
- dependency requires an alternative implementation
- original implementation strategy proves invalid

Return to Spec instead when:

- scope changes
- requirement changes
- material constraint changes
- acceptance criteria change
- user-visible intended behavior changes

All shown frontmatter fields are required. Use P-01, P-02, etc. in execution order; record dependencies where order alone is insufficient. Traceability references must resolve to the current Spec and Plan. Minor target or implementation-detail adjustments may be recorded in place; replan when they invalidate strategy, ordering, or verification.
