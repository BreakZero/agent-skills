# Plan contract

Use a plan when implementation choices, dependencies, handoff, or recovery need a shared record. Refer to the current Spec rather than copying it.

Include:

- The chosen approach and decisions that affect the implementation.
- Expected code, data, configuration, or runtime surfaces.
- Meaningful work units in dependency order, each with a concrete action and an observable completion condition.
- A verification path for every acceptance criterion and material constraint.

For auditable work, give work units stable IDs such as `P-01` and link them to requirement or acceptance IDs. Add prerequisites, risks, rollback, migration, or recovery detail only when it changes execution.

The plan is ready when another implementer can execute it without deciding the intended outcome, and its verification path covers the contract. Readiness is a quality judgment, not an approval round. Revise the plan if the strategy or validation path changes; return to the Spec if the outcome changes. Invalidate affected execution evidence after revision.

If information that could change the goal, scope, constraints, or acceptance criteria is missing, check the task card and designated sources first. If the answer depends on user intent or a business decision, ask the user a specific clarifying question. Until answered, record it as an open question or blocker; do not turn a model inference into a confirmed requirement. Routine implementation choices that do not change the intended outcome may be decided and recorded without user confirmation.
