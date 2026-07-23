# Split-Flap Display

A pure CSS mechanical split-flap character display that recreates the iconic airport/railway departure board with 3D CSS transforms and keyframe animations.

## What does this do?

Renders characters using stylized mechanical flap units with a realistic 3D flip animation. Each unit displays a front character on its upper half, and when in the flipping state, rotates to reveal a back character — mimicking the physical soundless click of real split-flap boards. Supports numbers, letters, multiple sizes, and countdown timer layouts.

## How is it used?

```html
<div class="sfd-display" role="marquee" aria-label="Display showing numbers 1 2 3">
  <span class="sfd-unit" aria-label="1">
    <span class="sfd-flap" data-front="1" data-back="7"></span>
    <span class="sfd-flap is-bottom" data-front="1" data-back="7" aria-hidden="true"></span>
  </span>
  <span class="sfd-unit" aria-label="2">
    <span class="sfd-flap is-flipping" data-front="2" data-back="8"></span>
    <span class="sfd-flap is-bottom" data-front="2" data-back="8" aria-hidden="true"></span>
  </span>
</div>
```

Each unit requires one `.sfd-flap` (top half) and one `.sfd-flap.is-bottom` (bottom half). The `data-front` attribute sets the currently displayed character and `data-back` sets the next character to flip to. Add `.is-flipping` to trigger the rotation animation.

### Size variants

| Class | Use case |
|-------|----------|
| (default) | Standard display — numbers and letters |
| `sfd-display--sm` | Compact scoreboard layouts |
| `sfd-display--md` | Medium display between default and small |
| `sfd-unit--letter` | Wider unit for uppercase letters |

### Separators

Use `.sfd-separator` for hour/minute/second labels in countdown timer layouts.

## Why is it useful?

Split-flap displays are instantly recognizable, emotionally engaging UI elements used everywhere from train stations to dashboard widgets. This implementation is useful for:

- **Countdown timers** and launch clocks
- **Scoreboards** in sports and gaming applications
- **Departure boards** in transportation apps
- **Visitors counters** and real-time metrics
- **Nostalgic/retro-themed UIs** needing character and personality

Fits EaseMotion's philosophy by demonstrating advanced CSS capabilities — 3D perspective transforms, `rotateX` keyframe animations, `transform-style: preserve-3d`, and `backface-visibility` — all orchestrated to create a mechanically convincing effect without a single line of JavaScript.
