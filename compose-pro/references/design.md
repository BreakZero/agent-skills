# Visual design in Compose

Use the product's design system as the source of truth. Material components and tokens are useful when the product adopts Material; a custom system can be equally valid.

- Check hierarchy, spacing, typography, color, and interaction states against the provided design or established screens.
- Prefer shared tokens for values that must stay consistent. A one-off literal is not automatically a defect.
- Verify adaptive layouts with the window sizes and postures the product supports. Avoid assuming one breakpoint or one navigation pattern fits every app.
- Check light and dark appearance when both are supported, including contrast and system bars.
- Treat animation as feedback for state or spatial change; respect the product's motion language and accessibility settings.

Official references: [Material 3 in Compose](https://developer.android.com/develop/ui/compose/designsystems/material3) and [adaptive layouts](https://developer.android.com/develop/ui/compose/layouts/adaptive).
