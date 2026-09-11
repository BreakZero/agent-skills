# Task Classification

Classify by uncertainty and consequence. File count alone is not complexity.

## Trivial

Use `execute → verify` for a mechanical, local change with negligible design
uncertainty, such as formatting, static copy, a rename, or a known constant.

## Simple

Use `inspect → execute → verify` when the desired behavior is clear after local
inspection and implementation requires no material product, architecture,
security, compatibility, or data decision. Examples include a localized bug
fix, known configuration change, or established UI adjustment.

Trivial and simple work need no persisted Spec or Plan by default.

## Complex

Use `spec → plan → execute → verify` when correctness depends on making the
contract explicit before implementation. Typical signals are:

- new or changed user-visible behavior;
- public API, data-model, architecture, migration, or security impact;
- several interacting requirements or acceptance conditions;
- a meaningful risk of implementing the wrong outcome.

## Exploratory

Use `research → spec → plan → execute → verify` only when a bounded technical,
product, architectural, or external-feasibility decision prevents a reliable
Spec. Research ends when that decision can be made or a concrete external
blocker is established.

## Reclassify when needed

Escalate the route when new information changes the contract or exposes a
decision that must be resolved first. A larger-than-expected implementation is
not enough by itself: update the Plan unless the outcome or acceptance contract
also changed.

If the task becomes trivial or simple after inspection, continue without manufacturing
Spec or Plan artifacts. Preserve artifacts already requested by the user or
needed for auditability.
