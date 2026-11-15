# Development notes

patternz is one file, `index.html`, containing the markup, styles and script. There is no build step and no framework. Edit the file and reload the browser.

## Layout of the file

The script is divided into commented sections. In order:

| Section | Key names | Role |
|---|---|---|
| Helpers | `clamp`, `lerp`, `sstep`, `mulberry32`, `makeNoise` | Math helpers, a seeded random generator and value noise (`fbm`). |
| Default state | `DEF` | Every setting and its default value. The whole app state is one flat object of this shape. |
| Control schema | `TABS`, `SCHEMA`, `SIZES`, `PALETTES`, `BLENDS` | Declares the settings panel: categories, groups and controls. |
| State, history, storage | `S`, `setState`, `commit`, `undo`, `redo`, `store` | The live state, undo stack and local-storage wrapper. |
| Field function | `makeField` | Builds the thickness map: a function `(x, y) → 0..1`. |
| Color picker | `colorPicker` | Chooses a fill for each shape from the color mode and palette. |
| Stripe generators | `profileFn`, `genStripes`, `genStripesPolar` | Produce stripe polygons for straight and circular layouts. |
| Dot generator | `shapePath`, `genDots` | Produces dot geometry for every grid type. |
| SVG assembly | `clipPolyRect`, `clipSegRect`, `shapeToD`, `buildLayer`, `buildSVG` | Clips geometry to the canvas and writes the SVG string. |
| Preview | `render`, `doRender`, `fit` | Draws the SVG into the page and scales it. |
| Controls | `buildControls`, `makeCtl`, `LBL`, `TIP`, `NOTES`, `ACC_META` | Builds the panel from the schema, with labels, tooltips and group notes. |
| Randomize and variations | `randomize`, `mutated`, `openVariations` | Random patterns and the variations grid. |
| Export | `EXPORTS`, `saveFile`, `rasterize`, `riskyEffects` | SVG, PNG and clipboard output. |
| Toolbar and shortcuts | event handlers | Wiring for buttons and keys. |

## How rendering works

1. `buildSVG(S)` is a pure function from a state object to an SVG string. The preview, thumbnails, variations and every export call it.
2. It calls `buildLayer`, which runs a generator (`genStripes`, `genStripesPolar` or `genDots`).
3. A generator walks its stripes or dots, asks the field function for a value at each position, and emits geometry through `add(color, geometry, isStroke)`. Geometry is either `{polys: [[x, y], …]}` or `{circle: [x, y, r]}`.
4. `buildLayer` groups geometry by color, clips each shape to the canvas rectangle, and writes one `<path>` per shape inside a `<g>` per color.

Two rules keep exported files portable across design tools:

- **No clip paths or masks.** Shapes are clipped in JavaScript (`clipPolyRect` for fills, `clipSegRect` for strokes), so no coordinate lies outside the canvas.
- **No transforms.** The second layer's rotation, scale and offset are applied to the points themselves through the `T` argument of `buildLayer`.

The only non-portable features are the Melt filter and CSS blend modes. `riskyEffects()` reports when they are active so the export menu can warn the user.

## Adding a setting

1. Add a key with its default to `DEF`.
2. Add a control to a group in `SCHEMA`, for example:
   ```js
   {k:'myValue', t:'range', min:0, max:1, step:.01, show:s=>s.mode==='stripes'}
   ```
   Control types are `range`, `select`, `seg`, `check`, `toggle` and `color`. `show` is optional and hides the control when it returns false.
3. Add a label in `LBL` and, if helpful, a tooltip in `TIP`. A label can be a function of the state.
4. Read `S.myValue` in the generator or in `buildSVG`.

Undo, saving, JSON import/export, variations and reset pick the new key up automatically, because they all work on the flat state object and the schema.

To add a group or category, add an entry to `SCHEMA` with a new `sec` name, or a new id to `TABS`. Group descriptions live in `NOTES` under the key `tabId/Group name`. The summary shown on a collapsed card comes from `ACC_META`.

## Adding a thickness map

Add a `case` to the `switch` in `makeField` that returns a value between 0 and 1 for the rotated, normalized coordinates `ru` and `rv`, then add the option to the `fType` control in `SCHEMA`.

## Storage

| Key | Contents |
|---|---|
| `opart.last` | The last session's state, restored on load. |
| `opart.saved` | Saved patterns, by name. |
| `patternz.acc` | Which cards are open. |

The `opart.` prefix predates the rename to patternz and is kept so existing saved patterns are not lost.

## Downloads

`saveFile` first looks for an optional host API (`window.claude.use('downloads')`), which exists only when the page is embedded as a Claude artifact. On a normal web page that API is absent and the function falls back to a standard `<a download>` link.

## Testing

There is no test suite. The checks used during development were:

- Load the page with a headless browser, apply a range of states with `setState(...)`, and assert there are no page errors.
- Parse the coordinates of an exported SVG and confirm none fall outside `0..W` and `0..H`.
- Render the same SVG with a browser, `rsvg-convert` and CairoSVG, and compare the images.
