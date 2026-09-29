# Accessibility in Compose

Inspect the semantics users actually receive. Material and Foundation components provide many defaults, so add semantics only where the resulting control lacks a useful label, state, role, or action.

- Give meaningful images and icon-only controls an accessible name. Use `contentDescription = null` for decorative images or an icon whose parent already supplies the label.
- Preserve a usable touch target, commonly at least 48 dp for interactive controls. Check the whole clickable area, not only the visible icon.
- Support font scaling and avoid clipping essential text at the supported display and font sizes.
- Check text contrast in the actual color combination. A theme token alone does not prove adequate contrast.
- Use heading, grouping, live-region, or custom-action semantics when they improve the reading and interaction order; avoid duplicate announcements.
- Verify changed custom controls with TalkBack or accessibility tests when static inspection cannot establish their behavior. Check motion settings for animations that can cause discomfort.

Official references: [Compose accessibility](https://developer.android.com/develop/ui/compose/accessibility) and [API defaults](https://developer.android.com/develop/ui/compose/accessibility/api-defaults).
