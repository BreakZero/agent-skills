# Spec contract

State the bounded outcome in terms that implementation and verification can share. Use the project's format; add stable IDs when multiple artifacts need traceability.

Include:

- Goal and in-scope deliverables. Name exclusions only when they resolve likely ambiguity.
- Observable requirements and material constraints, including compatibility or data limits.
- Acceptance criteria that can be checked against each requirement and material constraint.
- Assumptions or open questions only when they could change the outcome.

For larger auditable work, IDs such as `FR-01`, `C-01`, and `AC-01` make revisions and coverage explicit. A direct assertion is enough for a simple criterion; Given/When/Then can clarify conditional behavior.

The contract is ready when scope is bounded, consequential questions are resolved or stated as blockers, and each in-scope obligation has a checkable acceptance path. When intended behavior changes, revise the contract and invalidate affected plan or verification evidence. Preserve IDs whose meanings have not changed.
