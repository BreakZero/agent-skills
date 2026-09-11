# Plan Contract

The Plan turns a ready Spec into an executable strategy. It does not redefine
the requested outcome.

## Frontmatter

```yaml
---
type: plan
version: 2
id: PLAN-001
task: TASK-001
spec: SPEC-001
status: draft
---
```

Allowed `status`: `draft`, `ready`.

## Required content

### Objective and strategy

Reference the Spec, summarize the implementation objective, and record the
decisions that shape the approach. Do not restate the full Spec.

### Impacted areas

Name the files, modules, interfaces, data, configuration, or runtime surfaces
expected to change. Use a table only when comparison helps.

### Steps

Create the fewest meaningful implementation units that make dependencies,
handoff, or recovery clear. Each Step needs a stable `P-*` ID, an action-oriented
title, concrete targets and actions, the Spec IDs it covers, and a checkable
completion condition.

```markdown
### P-01 — <Action-oriented title>

**Targets:** <files, modules, interfaces, or runtime surfaces>

**Actions**
- <concrete operation>

**Covers:** FR-01, AC-01

**Done when:** <observable result and required evidence>
```

Add `Depends on`, `Preconditions`, `Outputs`, `Validation`, or `Failure /
Recovery` only when that information is not already clear from the Step and
materially affects execution. For structured tooling, use the equivalent keys
`id`, `title`, `depends_on`, `preconditions`, `targets`, `actions`, `outputs`,
`covers`, `validation`, `done_when`, and `failure_recovery`.

Split Steps when parts have different prerequisites, outputs, owners, or
recovery paths. Combine mechanical edits that succeed or fail together. Step
validation establishes local progress; final Verification still evaluates the
acceptance contract.

### Validation and traceability

State the smallest set of build, test, inspection, or runtime checks sufficient
to evaluate the Acceptance Criteria. Show that every requirement, material
constraint, and Acceptance Criterion has both an implementation path and a
verification path. Use a traceability table when the mapping is not obvious.

## Optional content

Add dependencies, risks, migration/compatibility, or rollback only when they
change execution or recovery decisions.

## Ready criterion

Set `status: ready` when:

- the referenced Spec is ready;
- Steps are executable in dependency order and have checkable completion bounds;
- all referenced IDs resolve and every in-scope Spec item is covered;
- every Acceptance Criterion has a verification path;
- no implementation decision remains that could change the Spec.

Readiness is a quality gate, not a separate approval round.

## Replanning

Revise the Plan when the strategy, targets, Step boundaries, dependencies, or
verification paths become invalid while the Spec remains correct. Return to the
Spec when intended behavior or its acceptance contract changes.

After a Plan revision, invalidate affected execution and verification evidence.
Preserve unchanged IDs; retire rather than recycle IDs with changed meaning.
