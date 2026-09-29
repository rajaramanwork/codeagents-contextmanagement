---
applyTo: "src/**/*.tsx,src/**/*.module.css"
description: "Design system usage — @enterprise/ui components and design tokens"
---
# Design system usage

- Check `@enterprise/ui` before creating any UI primitive. Common ones: `Button`, `IconButton`, `TextField`, `Select`,
  `Combobox`, `DatePicker`, `Dialog`, `Drawer`, `DataTable`, `Tabs`, `Toast`, `Skeleton`, `EmptyState`, `PageHeader`.
- Don't wrap a design-system component just to rename props or restyle it. If it's missing a capability, open an
  issue on the design-system repo and note it in the PR.
- Layout with `Stack`, `Grid`, `Inline` from `@enterprise/ui` — not ad-hoc flexbox utility classes.
- Styling: CSS Modules only, using tokens: `var(--ent-color-*)`, `var(--ent-space-*)`, `var(--ent-font-*)`, `var(--ent-radius-*)`.
- Never hard-code hex/rgb colors, px spacing, or font families. No inline `style={{...}}` except for dynamic values
  (e.g. computed widths).
- Support light/dark themes and density via tokens only — never branch on theme in component code.
- Icons from `@enterprise/icons` only; decorative icons get `aria-hidden`.
- Responsive: mobile-first; use token breakpoints (`--ent-bp-md`, `--ent-bp-lg`).

```css
/* OrderSummary.module.css */
.meta {
  gap: var(--ent-space-2);
  color: var(--ent-color-text-subtle);
  font: var(--ent-font-body-sm);
}
```
