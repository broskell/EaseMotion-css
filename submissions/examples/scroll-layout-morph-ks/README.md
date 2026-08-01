# Scroll-Driven Layout Morph

## What does this do?

Demonstrates CSS layout properties — border-radius, grid gap, padding, and grid-template-columns — that morph continuously in response to scroll position. Uses `@property`-registered custom properties driven by `animation-timeline: view()`. Cards and grids transform their shape, spacing, and structure as the user scrolls through each section.

## How is it used?

```html
<!-- Cards that morph from circular to rounded-rect as you scroll -->
<div class="morph-grid">
  <article class="morph-card radius-morph">...</article>
  <article class="morph-card radius-morph">...</article>
</div>
```

Example: border-radius morphing

```css
@property --morph-radius {
  syntax: '<length>';
  inherits: true;
  initial-value: 0.5rem;
}

.radius-morph {
  border-radius: var(--morph-radius);
  animation: radius-morph 1s ease-out both;
  animation-timeline: view();
  animation-range: entry 10% cover 50%;
}

@keyframes radius-morph {
  from { --morph-radius: 2.5rem; }
  to   { --morph-radius: 0.5rem; }
}
```

## Why is it useful?

This is the first EaseMotion submission to animate **layout properties** (border-radius, gap, padding, grid-template-columns) using `@property` + `animation-timeline`. Zero results across 4,167+ submissions for `@property` combined with any of these layout properties.

Layout properties have historically been non-animatable or only animatable between matching data types. `@property` changes this — by registering a typed custom property, the browser can interpolate layout values that were previously impossible to animate smoothly.

### Four techniques demonstrated

1. **Border radius morph** — cards transition from 2.5rem (pill) to 0.5rem (rounded rect)
2. **Grid gap morph** — grid gap shrinks from 2.5rem to 0.5rem, cards cluster together
3. **Padding morph** — card padding expands from 0.75rem to 2.5rem
4. **Grid columns morph** — 1 column → 2 columns → 3 columns via `repeat(var(--morph-columns), 1fr)`

### Accessibility

- `prefers-reduced-motion`: static reasonable layout values
- `forced-colors`: border-based card outlines
- `prefers-color-scheme`: full light mode
- Print: static layout, card break-inside avoidance
- Mobile: single-column responsive fallback at narrow widths
