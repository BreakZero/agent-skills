# Compose performance

Identify a user-visible cost or a measured hot path before recommending optimization. Check release-like behavior when debug overhead could change the conclusion.

- `remember` can cache expensive calculations when inputs are stable and keys are correct. `derivedStateOf` helps when frequently changing snapshot state maps to a less frequently changing UI value; it is not a general replacement for filtering or sorting.
- Investigate recomposition with Layout Inspector or compiler reports before adding stability annotations. `@Stable` and `@Immutable` are contracts about behavior, not automatic speed switches. Account for strong skipping in the project's compiler version.
- Use lazy layouts and stable item keys where collection size and identity warrant them. Avoid changing data structures solely because a parameter is reported unstable without evidence of a problem.
- For startup or jank, measure with Macrobenchmark and create an app-specific Baseline Profile for critical journeys when it helps. Compose already ships a library Baseline Profile; do not add hand-written blanket keep rules as a performance fix.
- Match image loading, sizing, and caching to the view's actual display size.

Official references: [performance best practices](https://developer.android.com/develop/ui/compose/performance/bestpractices), [strong skipping](https://developer.android.com/develop/ui/compose/performance/stability/strongskipping), and [Baseline Profiles](https://developer.android.com/develop/ui/compose/performance/baseline-profiles).
