# Verification Contract

Verification determines whether the implementation satisfies the Spec.

Plan completion alone is not proof of correctness.

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

Allowed `status` values:

- in_progress
- complete

---

## Required Sections

# Verification: <Title>

## Acceptance Criteria

Verify every Acceptance Criterion from the Spec.

Recommended format:

| ID | Result | Evidence | Notes |
|---|---|---|---|
| AC-01 | PASS | integration test | |
| AC-02 | PASS | streaming API request | |
| AC-03 | FAIL | regression test | existing test failure |

Allowed result values:

- PASS
- FAIL
- BLOCKED

`PASS` requires evidence.

`FAIL` must describe the observed deviation.

`BLOCKED` must identify the blocker.

---

## Validation Evidence

Record only validation actually performed.

Examples:

### Build

```text
Command: npm run build
Result: PASS
```

### Tests

```text
Command: npm test
Result: 42 passed, 0 failed
```

### Manual

```text
Check: streaming response delivers incremental chunks
Result: PASS
```

Never claim validation that was not actually performed.

---

## Deviations

Include only when implementation differs from the Spec.

Recommended format:

```markdown
### D-01

Expected:
...

Observed:
...

Impact:
...

Action:
FIX | REPLAN | SPEC_REVISION
```

---

## Final Decision

Exactly one final decision is required when `status: complete`. While assessment is still in progress, omit the Final Decision section:

```text
DONE
FIX_REQUIRED
REPLAN_REQUIRED
SPEC_REVISION_REQUIRED
```

### DONE

Use only when all required Acceptance Criteria pass.

Transition:

VERIFYING → DONE

### FIX_REQUIRED

Use when implementation is incorrect but the Spec and Plan remain valid.

Transition:

VERIFYING → EXECUTING

### REPLAN_REQUIRED

Use when the Spec remains valid but the implementation strategy is no longer appropriate.

Transition:

VERIFYING → PLAN_DRAFT

### SPEC_REVISION_REQUIRED

Use when the intended scope, requirements, constraints, or Acceptance Criteria must change.

Transition:

VERIFYING → SPEC_DRAFT

## Evidence and Blocked Assessments

All shown frontmatter fields are required for the full workflow. Evidence must identify the actual command or inspection, observed result, and relevant target or artifact; a test name alone is not proof. Link retained logs/screenshots when available. Include every current AC once. During an unfinished pass, unverified rows use BLOCKED with a concrete explanation such as `not yet run`; this alone does not make the workflow BLOCKED if the agent can continue.

If a required check cannot run due to an external dependency, keep Verification in_progress, omit Final Decision, and set workflow BLOCKED with blocked_from VERIFYING. Do not reinterpret missing access as a failed implementation. If other findings already establish required fixes or revision, a complete assessment may issue that non-DONE decision while retaining blocked rows and limitations. DONE requires all ACs PASS with current evidence and no unresolved blockers.

If multiple deviations exist, select the earliest stage that must be revisited: SPEC_REVISION_REQUIRED before REPLAN_REQUIRED before FIX_REQUIRED. Never weaken ACs merely to obtain PASS.
