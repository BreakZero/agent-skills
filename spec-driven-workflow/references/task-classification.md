# Task Classification

Classify the task before choosing the workflow.

## Trivial

Use when the requested change is mechanical, local, and has negligible design uncertainty.

Examples:

- rename a file
- fix formatting
- change static copy
- update a known constant

Workflow:

Execute → Verify

---

## Simple

Use when implementation requires inspecting existing behavior but does not require material product or architectural decisions.

Examples:

- fix a localized bug
- resolve a compiler warning
- adjust an existing UI behavior
- modify a known configuration

Workflow:

Inspect → Execute → Verify

---

## Complex

Use when correctness depends on explicitly defining requirements before implementation.

Typical signals include:

- multiple modules or files
- new user-visible behavior
- new API or API behavior change
- data model change
- architecture change
- security-sensitive behavior
- migration or compatibility concern
- multiple acceptance conditions

Workflow:

Spec → Plan → Execute → Verify

---

## Exploratory

Use when important unknowns must be resolved before requirements can be reliably defined.

Typical signals include:

- architecture selection
- external API feasibility
- library or framework selection
- unclear product behavior
- technical feasibility investigation
- competing solution approaches

Workflow:

Research → Spec → Plan → Execute → Verify

---

## Escalation Rule

Always choose the lightest workflow that preserves correctness.

Escalate when newly discovered complexity materially affects:

- scope
- architecture
- public API
- data model
- security
- user-visible behavior
- acceptance criteria

Examples:

Simple → Complex

when a local bug fix requires changing public API behavior.

Complex → Exploratory

when implementation depends on unresolved technical feasibility.

Do not downgrade merely to avoid producing a Spec or Plan.
