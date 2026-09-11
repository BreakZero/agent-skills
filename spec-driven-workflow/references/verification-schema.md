# Verification Contract

Verification determines whether the implementation satisfies the current Spec.
Plan completion alone is not evidence of correctness.

## Frontmatter

```yaml
---
type: verification
version: 1
id: VERIFY-001
task: TASK-001
spec: SPEC-001
plan: PLAN-001
status: in_progress
---
```

Allowed `status`: `in_progress`, `complete`. Omit `plan` when no Plan exists.

## Acceptance results

Evaluate every current `AC-*` exactly once:

| ID | Result | Evidence | Notes |
|---|---|---|---|
| AC-01 | PASS | `<command>`: observed result | |

Allowed results:

- `PASS` — fresh evidence demonstrates the criterion.
- `FAIL` — observed behavior contradicts the criterion.
- `BLOCKED` — an external dependency prevents the check.

Evidence names what was run or inspected, the observed result, and the relevant
target. Record only checks actually performed. Retained logs or screenshots may
support the record but are not required when the observation is concise and
reproducible.

When a Plan exists, reconcile incomplete or changed `P-*` Steps before issuing a
final decision. Do not duplicate Step evidence that adds nothing to the
Acceptance Criterion result.

## Deviations

For each material mismatch, record expected behavior, observed behavior, impact,
and the earliest corrective stage:

- `FIX_REQUIRED` — implementation is wrong; Spec and Plan remain valid.
- `REPLAN_REQUIRED` — Spec remains valid; implementation strategy must change.
- `SPEC_REVISION_REQUIRED` — the intended contract must change.

## Final decision

When assessment is complete, set `status: complete` and record exactly one:

```text
DONE
FIX_REQUIRED
REPLAN_REQUIRED
SPEC_REVISION_REQUIRED
```

Use `DONE` only when every applicable Acceptance Criterion passes with current
evidence and no material blocker remains. Otherwise choose the earliest stage
that must change. Keep Verification `in_progress` when an external blocker is
the only reason assessment cannot finish.

After any implementation, Plan, or Spec change, rerun the checks whose evidence
may no longer be valid. Historical evidence may remain labeled as history; it
cannot prove the changed result.
