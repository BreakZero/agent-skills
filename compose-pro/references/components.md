# Composable structure and effects

Separate UI description from business rules when doing so clarifies ownership or makes behavior testable. Keep related small composables together; extract a component when it has a distinct responsibility or repeated use, not because of line count.

- Expose `modifier` and callbacks where callers need composition and control. Use slots when callers truly need variable UI content.
- Keep event handlers near the interaction when simple; move domain work to the appropriate state holder or use case.
- Choose effect APIs by lifecycle: `LaunchedEffect` for keyed coroutine work, `DisposableEffect` for setup with cleanup, and `SideEffect` for publishing state after each successful composition. Check keys and cleanup against the intended lifetime.
- Use lazy layouts for long or unknown-size collections. Add stable keys when item identity matters; use `contentType` when mixed item types benefit from reuse.
- Add previews for states whose visual behavior is hard to inspect otherwise. Verify important interactions in a running app or tests when previews cannot establish them.

Official references: [thinking in Compose](https://developer.android.com/develop/ui/compose/mental-model) and [side effects](https://developer.android.com/develop/ui/compose/side-effects).
