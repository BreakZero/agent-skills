# Kotlin in Compose code

Use the project's Kotlin version, compiler settings, and established style. Raise a Kotlin finding when it affects correctness, clarity, or maintainability in the requested scope.

- Model nullable and immutable data according to actual invariants. Avoid converting every nullable operation to a scope function or every conditional to `when`.
- Tie coroutines to the appropriate lifecycle. Check cancellation, exception handling, and stale captures in UI-triggered or ViewModel work.
- Choose `StateFlow`, `SharedFlow`, channels, callbacks, or ordinary suspend functions by delivery and replay needs; no one type is universally right for events.
- Use inline, contracts, aliases, and extensions only when they clarify a real API or performance need.
- Check public API compatibility before replacing overloads, changing types, or adopting newer language features.

Official references: [Kotlin on Android](https://developer.android.com/kotlin) and [coroutines on Android](https://developer.android.com/kotlin/coroutines).
