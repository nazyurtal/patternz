# Changelog

Notable changes to patternz, newest first. No versions have been tagged yet.

## Unreleased

### Added
- Stripe patterns (vertical, horizontal) and dot patterns (square, honeycomb, circular grids).
- Circular stripe layouts: rings and rays, with an optional empty center and a movable center point.
- Ten thickness maps, with randomness, contrast, balance, levels and invert.
- Stripe pieces with lens, wedge, hourglass and stepped tapers.
- Waves, random bending, liquid distortion and ripples.
- Palettes, gradients, hex color input and a transparent background option.
- Second layer for moiré effects.
- Variations grid with three strength levels.
- Drag on the canvas to move the center.
- Undo and redo, saved patterns with thumbnails, JSON import and export.
- Export as SVG, flattened SVG and PNG (1×, 2×, 4×); copy to clipboard as SVG or PNG.
- Preview zoom, focus mode and a keyboard shortcut list.
- Responsive layout for desktop, tablet and phone.

### Changed
- Renamed the project from "Op-Art Pattern Generator" to "patternz".
- Settings regrouped into Layout, Thickness, Pieces, Dot shape, Waves & bending, Color, Effects, Second layer, Canvas and Saved patterns, with plain-language labels and a short description per group.
- Interface set in Inter throughout, with simplified icons.

### Fixed
- Exported SVGs no longer rely on clip paths or transforms, so they open correctly in design tools that handle those differently.
- Rings no longer show a break where the circle closes when waves are applied.
- Downloads work on a regular web page without showing the SVG code dialog.
