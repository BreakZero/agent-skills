---
name: compose-pro
description: Review or improve Jetpack Compose UI code when the task calls for Compose-specific correctness, accessibility, or performance judgment.
metadata:
  author: Compose Agent Skill
  version: "1.0"
  license: MIT
---

# Compose Pro

Use the project's Android and Kotlin versions, design system, architecture, and conventions as the baseline. Follow the user's requested scope. For an edit, make the change and verify the affected behavior; for a review, report actionable findings supported by the code. A reference is a decision aid, not a checklist of violations.

Read only the references relevant to the task:

| Concern | Reference |
| --- | --- |
| Compose APIs and compatibility | [api.md](references/api.md) |
| Composable structure and effects | [components.md](references/components.md) |
| State ownership and persistence | [state.md](references/state.md) |
| Navigation and back stack | [navigation.md](references/navigation.md) |
| Theming and visual design | [design.md](references/design.md) |
| Semantics and input access | [accessibility.md](references/accessibility.md) |
| Measured performance | [performance.md](references/performance.md) |
| Kotlin and coroutine semantics | [kotlin.md](references/kotlin.md) |
| Build and code hygiene | [hygiene.md](references/hygiene.md) |

For version-sensitive APIs, check the project's dependencies and current Android documentation before recommending a migration. Prefer a concrete defect, regression risk, or demonstrated performance cost over a stylistic preference. Preserve deliberate architecture and library choices unless the user asks to change them.

In a review, give each finding a location, its effect, and a feasible fix. Prioritize by user impact; omit files without findings. Show replacement code only when it clarifies a non-obvious fix. In an edit, summarize what changed and the checks actually run.
