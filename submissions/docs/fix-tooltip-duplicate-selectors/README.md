# Fix Duplicate Selectors in Tooltip Component

## What does this do?

Fixes two duplicate CSS selectors in `components/tooltips.css` (`line 340` and `line 346`) that cause `stylelint` `no-duplicate-selectors` errors. The duplicated selectors `.ease-tooltip[data-animation="3d-flip"]` and `.ease-tooltip[data-animation="3d-flip-scale"]` are already defined earlier in the file (lines 237 and 257). Their custom property declarations are merged into the first definitions and the duplicate blocks are removed.

## How is it used?

No usage change — the fix consolidates duplicate selectors so that linting passes cleanly. The affected classes still work identically:

```html
<span class="ease-tooltip" data-tooltip="Hello!" data-animation="3d-flip">Hover me</span>
<span class="ease-tooltip" data-tooltip="Hello!" data-animation="3d-flip-scale">Hover me</span>
```

## Why is it useful?

Running `npm run lint` currently produces 2 errors:

```
components/tooltips.css
  340:3  ✖  Duplicate selector ".ease-tooltip[data-animation="3d-flip"]"
  346:3  ✖  Duplicate selector ".ease-tooltip[data-animation="3d-flip-scale"]"
```

This blocks a clean CI lint pass. The fix merges the custom property definitions from the duplicate blocks into the original selector blocks and removes the duplicates, restoring clean linting while preserving all existing behavior and specificity.
