# Spec Contract

The Spec defines what must be true when the task is complete.

It must not describe implementation details unless they are explicit constraints.

## Frontmatter

Required:

```yaml
---
type: spec
version: 1
id: SPEC-001
task: TASK-001
status: draft
---
```

Allowed `status` values:

- draft
- ready

Do not invent additional values.

---

## Required Sections

# Spec: <Title>

## Goal

State the desired outcome clearly and concisely.

## Scope

### In Scope

Define what this task must deliver.

### Out of Scope

Include only when explicit exclusions are needed to prevent scope ambiguity.

## Requirements

Use stable IDs.

```text
FR-01: ...
FR-02: ...
```

Use non-functional requirements only when relevant:

```text
NFR-01: ...
```

Requirements must describe observable or enforceable behavior.

## Acceptance Criteria

Use stable IDs:

```text
AC-01: ...
AC-02: ...
```

Each Acceptance Criterion must be objectively verifiable.

Use Given / When / Then when useful for behavioral requirements, but do not force that format when a simpler testable statement is clearer.

---

## Conditional Sections

Include only when materially relevant.

### Context

Relevant existing behavior, architecture, or background.

### Constraints

Use IDs when constraints materially influence implementation.

```text
C-01: ...
```

Examples:

- architecture must remain unchanged
- no breaking public API changes
- SwiftUI only
- existing persistence format must remain compatible

### Behavior Rules

Rules that clarify interactions between requirements.

### Edge Cases

Important boundary or failure conditions.

### Assumptions

Assumptions required to proceed.

### Open Questions

Only unresolved questions that are worth recording.

Do not mark the Spec `ready` while a material open question remains.

---

## Readiness Rules

A Spec may transition from `draft` to `ready` only when:

1. Goal is explicit.
2. In-scope behavior is bounded.
3. Requirements are sufficiently testable.
4. Material constraints are captured.
5. Acceptance Criteria cover the expected in-scope outcome.
6. No unresolved question could materially change:
   - scope
   - architecture
   - public API
   - data model
   - security
   - user-visible behavior
   - acceptance criteria

Minor ambiguity may be resolved with a documented reasonable assumption.

Material ambiguity blocks readiness.

---

## ID Rules

Required stable IDs:

- `FR-*` — functional requirement
- `NFR-*` — non-functional requirement
- `AC-*` — acceptance criterion

Use `C-*` for material constraints when useful.

Do not assign IDs to every paragraph or bullet.

IDs exist for traceability, not decoration.

---

## Minimal Example

```markdown
---
type: spec
version: 1
id: SPEC-001
task: TASK-001
status: ready
---

# Spec: Add Streaming AI Relay

## Goal

Expose an OpenAI-compatible streaming relay using the existing backend architecture.

## Scope

### In Scope

- Add the relay endpoint.
- Support streaming responses.
- Use the configured default provider.

### Out of Scope

- Provider fallback.
- Conversation persistence.

## Requirements

- FR-01: The API must expose an OpenAI-compatible chat completion endpoint.
- FR-02: The endpoint must support streaming responses.

## Constraints

- C-01: Existing backend module architecture must remain intact.
- C-02: Existing public endpoints must not change.

## Acceptance Criteria

- AC-01: A valid request returns an OpenAI-compatible response.
- AC-02: A streaming request delivers incremental response chunks.
- AC-03: Existing API integration tests continue to pass.
```

## Coverage Invariant

Every FR/NFR and material constraint must be demonstrable through one or more ACs. Reference covered item IDs in each AC, for example `AC-01 (FR-01, C-01): ...`. Check coverage before marking ready; do not defer missing requirements to Verification. Use sequential IDs such as FR-01, NFR-01, AC-01 and C-01, preserving them across edits. Required sections must contain substantive content; omit irrelevant conditional sections.
