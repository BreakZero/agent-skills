---
name: spec-driven-workflow
description: >
  Manage non-trivial AI tasks through a controlled
  Spec → Plan → Execute → Verify workflow.
  Use for feature development, architecture changes,
  refactoring, multi-file changes, and other tasks
  where requirements and implementation should be separated.
---

# Spec Driven Workflow

## Purpose

Ensure that AI understands what must be done before deciding how to implement it.

The canonical workflow is:

Request
→ Classify
→ Research if required
→ Spec
→ Plan
→ Execute
→ Verify
→ Done

The Spec defines what is correct.

The Plan defines how to implement it.

Verification evaluates the implementation against the Spec, not merely against Plan completion.

---

## Core Rules

1. Classify the task before selecting the workflow.
2. Do not create a Plan from a materially ambiguous Spec.
3. Do not silently change the Spec during execution.
4. Re-plan when implementation strategy changes but requirements remain valid.
5. Return to Spec when scope, requirements, constraints, or acceptance criteria materially change.
6. Verify against Acceptance Criteria.
7. Keep artifacts minimal. Omit non-applicable optional sections.
8. Do not create empty sections.
9. Do not load every reference file by default. Read only the reference required by the current stage.

---

## Workflow

### 1. Classify

Read:

`references/task-classification.md`

Choose one workflow:

- trivial → Execute → Verify
- simple → Inspect → Execute → Verify
- complex → Spec → Plan → Execute → Verify
- exploratory → Research → Spec → Plan → Execute → Verify

---

### 2. Research

Research is optional.

Use it only when unresolved external, architectural, product, or technical uncertainty prevents a reliable Spec.

Read:

`references/research-schema.md`

Research must produce a decision or clearly identify a blocker.

Research findings feed into Spec.

Do not skip directly from Research to Plan.

---

### 3. Spec

Read:

`references/spec-schema.md`

The Spec defines:

- goal
- scope
- requirements
- material constraints
- acceptance criteria

Do not create an implementation Plan until the Spec satisfies the readiness rules.

---

### 4. Plan

Read:

`references/plan-schema.md`

Create the implementation Plan from the ready Spec.

The Plan must describe:

- implementation strategy
- impacted areas
- implementation steps
- validation strategy
- traceability to the Spec

Do not repeat the Spec as implementation steps.

---

### 5. Execute

Execute the ready Plan within the user's existing authorization. Readiness is a quality gate, not a mandatory approval round. Ask only for a material unresolved decision or an action that actually requires additional authorization. Respect requests to stop after research, Spec, or Plan; do not implement a planning-only request.

During execution:

Minor implementation detail changes:
→ continue execution

Implementation strategy becomes invalid:
→ return to Plan

Requirement, scope, constraint, or acceptance criteria changes:
→ return to Spec

Never silently modify the Spec to match the implementation.

---

### 6. Verify

Read:

`references/verification-schema.md`

Verify the implementation against every Acceptance Criterion.

A completed Plan is not sufficient evidence of correctness.

Verification must produce one final decision:

- DONE
- FIX_REQUIRED
- REPLAN_REQUIRED
- SPEC_REVISION_REQUIRED

---

## State Management

Read:

`references/workflow-state.md`

Use workflow state as the canonical source for:

- current stage
- artifact references
- blockers
- next action

When asked to check status, derive the answer from workflow state rather than reconstructing progress from conversation history.

## Working Artifacts

Read `references/workflow-state.md` when starting or resuming work. Keep task artifacts outside the installed skill directory. Use existing project conventions; otherwise use `work/spec-driven-workflow/<task-id>/` in the authorized workspace. For trivial/simple work, a compact state and verification summary in the conversation suffices unless persistence is requested. Do not manufacture Spec or Plan artifacts for those paths.

On resume, read state and referenced artifacts, then confirm they still match the current work before continuing. Domain skills and tools implement the work; this skill governs stages and output contracts. Follow applicable storage and access rules, including MCP-only vault access when required. Write human-readable content in the user's language; keep schema keys, IDs, and enums unchanged.
