# Compose navigation

Follow the project's navigation library and version. Check current library documentation before proposing typed routes, deep links, or a migration.

- Keep navigation decisions and back-stack behavior explicit. Screen UI can receive navigation callbacks when that improves reuse and testability.
- Check destination arguments, saved state, and deep-link inputs for validity and restoration behavior.
- For tabs, dialogs, and sheets, choose local state or navigation destinations based on whether they need a back-stack entry, restoration, or deep link.
- Check `launchSingleTop`, `popUpTo`, and state restoration against the intended user journey; they are not universal defaults.
- Test navigation paths with meaningful back, process restoration, and deep-link cases when changed.

Official reference: [Navigation with Compose](https://developer.android.com/develop/ui/compose/navigation).
