# State ownership and persistence

Place state at the lowest owner that needs to read and change it. Use a ViewModel for screen state when lifecycle, asynchronous work, or business behavior warrants it; keep transient component state local when simpler.

- Hoist state when multiple components coordinate or a caller must control it. Prefer values and events at reusable UI boundaries.
- Use `remember` for composition lifetime and `rememberSaveable` for small saveable UI state that must survive recreation. Use `SavedStateHandle` for ViewModel state that must be restored after process recreation.
- Collect streams with lifecycle awareness in Android UI. Keep mutable state private to its owner when exposing it outward.
- Use `derivedStateOf` when rapidly changing snapshot state produces a less frequently changing UI value. For expensive work from ordinary inputs, consider `remember` with correct keys or moving work upstream.
- Check effect keys, state capture, and one-time events against actual lifecycle behavior rather than mandating one event-stream type.

Official references: [state in Compose](https://developer.android.com/develop/ui/compose/state) and [state holders](https://developer.android.com/develop/ui/compose/state-hoisting).
