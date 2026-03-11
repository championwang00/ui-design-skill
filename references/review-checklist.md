# UI Review Checklist

## 10 Must-Check Items

When reviewing UI code, always verify:

- [ ] No layout shift on dynamic content
- [ ] Animations have `prefers-reduced-motion` support
- [ ] Touch targets are 44px minimum
- [ ] Hover effects disabled on touch devices (`@media (hover: hover)`)
- [ ] Keyboard navigation works properly (tab order, focus management)
- [ ] Icon buttons have aria labels
- [ ] Forms submit with Enter/Cmd+Enter
- [ ] Inputs are 16px+ to prevent iOS zoom
- [ ] No `transition: all` — specify exact properties
- [ ] z-index uses fixed scale or `isolation: isolate`

## Common Mistakes → Fixes

| Mistake                     | Fix                                               |
| --------------------------- | ------------------------------------------------- |
| `transition: all`           | Specify exact properties                          |
| Hover effects on touch      | Use `@media (hover: hover) and (pointer: fine)`   |
| Font weight change on hover | Use consistent weights, change color instead      |
| Animating `height`/`width`  | Use `transform` and `opacity` only                |
| No reduced motion support   | Add `prefers-reduced-motion` query                |
| z-index: 9999               | Use fixed scale or `isolation: isolate`           |
| Custom page scrollbars      | Only customize scrollbars in small elements       |
| `<div onClick>`             | Use `<button>` for interactive elements           |
| No form wrapper             | Wrap inputs in `<form>` for Enter submission      |
| Fade on scrollable content  | Remove fade — it cuts off content                 |
| Dark mode via `dark:` class | Use CSS variables that flip with theme            |
| Scroll animations (fade-up) | Don't — no scroll-triggered animations            |
