# Compose API and compatibility

Inspect the project's Kotlin, Compose compiler, Compose BOM, AndroidX, and minSdk versions before recommending an API change. Check current Android documentation when the recommendation depends on a release or deprecation. A newer API alone is not a review finding.

- Use the project's Material system. Material 3 is a reasonable choice for a new Material app; migration from Material 2 is a product and compatibility decision.
- Prefer lifecycle-aware Flow collection on Android screens when the dependency is available. Preserve other observable-state integrations that already meet lifecycle and behavior needs.
- Use `rememberSaveable` for small UI state that should survive activity recreation or process recreation. Confirm that values can be saved; use a `Saver` when needed.
- Use foundation pager, layout, and window-inset APIs supported by the project's versions. Check edge-to-edge behavior in the actual screen before changing padding.
- Choose animation APIs by behavior: `animate*AsState` for a target value, `AnimatedVisibility` or `AnimatedContent` for content transitions, and `Animatable` when direct control is needed.

Official references: [Compose state](https://developer.android.com/develop/ui/compose/state), [side effects](https://developer.android.com/develop/ui/compose/side-effects), and [AndroidX releases](https://developer.android.com/jetpack/androidx/versions).
