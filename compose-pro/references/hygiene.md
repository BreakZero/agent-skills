# Build and code hygiene

Follow repository conventions for packages, files, imports, formatting, documentation, dependencies, and CI. Suggest a new tool or project-wide reorganization only when the user requests it or a concrete problem requires it.

- Keep related UI and state-holder code discoverable. A file may contain several related composables; size alone is not a defect.
- Remove unused code and imports introduced by the change. Document non-obvious public contracts and business rules where needed.
- Keep secrets out of source control and shipped client code. `BuildConfig` fields are packaged into the app and do not make secrets safe.
- Use the existing build, lint, and test tasks needed to verify the changed behavior. Add targeted tests when they cover a material risk; avoid mandatory screenshot, coverage, release, or CI work for a local edit.
- Check release shrinking and Baseline Profile changes against measured behavior and current Android guidance. Do not add blanket Compose `-keep` rules.

Official references: [Android build overview](https://developer.android.com/build) and [app security](https://developer.android.com/privacy-and-security/security-best-practices).
