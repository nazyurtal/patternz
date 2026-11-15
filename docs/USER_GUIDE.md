# User guide

This guide explains every setting in patternz, in the order the settings panel shows them.

## How a pattern is built

A pattern has three ingredients:

1. **A layout**: stripes or dots, and how they are arranged.
2. **A thickness map**: an invisible image that says "thick here, thin there". Each stripe or dot reads its size from this map at its own position.
3. **Styling**: pieces, distortion, color and effects applied on top.

Most of the op-art look comes from the thickness map. If a pattern looks flat, change the map first.

## Toolbar

| Control | What it does |
|---|---|
| Undo / Redo | Step backward and forward through your changes. |
| Randomize | Rolls a completely new pattern in the current type. |
| Variations | Shows the current pattern next to seven alternatives. Pick one to apply it; new alternatives are generated around your pick. Choose Subtle, Medium or Wild to control how far they stray. |
| Seed | Rerolls only the random parts (noise, random colors). |
| Shortcuts (`?`) | Lists keyboard shortcuts. |
| Focus mode | Hides the settings panel. |
| Zoom | Fit, 50%, 100% or 200%. At 100% you see the true pixels of the export. |
| Copy | Copies the pattern as SVG or PNG. |
| Export | Downloads SVG or PNG. |

Each category in the panel is a card. Click a card's title to open or close it; the text on the right summarizes its current state. **Expand all** opens every card.

## Layout

**Pattern type**: *Stripes* draws lines of changing thickness. *Dots* draws a grid of shapes of changing size.

### Stripes

| Setting | Meaning |
|---|---|
| Direction | Vertical, Horizontal, Rings (concentric circles) or Rays (lines from the center outward). |
| Number of stripes | How many lines fit on the canvas. |
| Empty center size | Rings and Rays only. Leaves the middle blank. 0 means no hole. |
| Center · left ↔ right, up ↔ down | Rings and Rays only. Position of the center. You can also drag on the canvas. |

### Dots

| Setting | Meaning |
|---|---|
| Grid | Square, Honeycomb (offset rows) or Circular (rings of dots). |
| Distance between dots | Grid spacing in pixels. |
| Empty center size | Removes dots inside a circle. |
| Center | Position of the empty circle and of the Circular grid. |

## Thickness (Dot size in Dots mode)

### Range

| Setting | Meaning |
|---|---|
| Thinnest / Thickest | Stripe width at the two extremes, as a fraction of the space each stripe has. At 1 a stripe touches its neighbour; above 1 they overlap. |
| Thickness grows from | *Both sides* swells symmetrically. The *One side* options keep one edge straight. *Alternating sides* flips this on every other stripe. |
| Smallest / Largest dot | Dot size at the two extremes, relative to the grid spacing. |
| Random size | Adds per-dot size variation. |

### Where it changes

**Thick & thin follows** picks the shape of the thickness map:

| Option | Result |
|---|---|
| Soft waves | Smooth bands across the canvas. |
| Gradual | Thin on one side, thick on the other. |
| Big in the center, small at the edges | A radial falloff. |
| Circular ripples | Concentric rings of thick and thin. |
| Diamond ripples | The same, with diamond shapes. |
| Spiral | Rotating arms. |
| Random clouds | Organic blotches. |
| A single band / path | One thick path across the canvas. |
| Random blocks | A grid of cells with random values. |
| Even everywhere | No variation; everything at maximum. |

Depending on the option, these appear:

| Setting | Meaning |
|---|---|
| Repeats / Detail / Columns | How many times the shape repeats. |
| Repeats (other direction) / Number of arms / Rows | The second repeat count, where it applies. |
| Position | Slides the shape along its direction. |
| Angle | Rotates the map. |
| Center | Middle point for the radial options. |
| Band width, Edge softness, Curviness, Tilt, Move band, Stair steps | Shape of the single band. Stair steps turns a smooth path into steps. |

### Randomness

**Add randomness** mixes random blotches into the map. **Randomness detail** sets their size.

### Fine-tune

| Setting | Meaning |
|---|---|
| Contrast | Pushes values toward the two extremes. |
| Balance | Below 1, more of the canvas is thick. Above 1, more is thin. |
| Number of levels | Limits the map to a few fixed values for a stepped look. 0 keeps it smooth. |
| Swap thick and thin | Inverts the map. |

## Pieces (Stripes only)

| Setting | Meaning |
|---|---|
| Pieces per stripe | Cuts each stripe into this many segments along its length. |
| Offset between neighbours | Slides the pieces of each next stripe along, like bricks. |
| Gap between pieces | Space between segments. |
| Taper | How a piece narrows: Straight, Lens, Wedge, Hourglass or Stepped. |
| Sharpness | How strongly the taper is applied. |
| Keep each piece one thickness | On: each piece reads the map once, giving a blocky look. Off: thickness varies smoothly along the piece. |

Lens-shaped pieces with an offset of 0.5 give the classic woven look.

## Dot shape (Dots only)

| Setting | Meaning |
|---|---|
| Dot shape | Circle, Diamond, Rounded square, Square, Line, Cross or Triangle. |
| Stretch | Width-to-height ratio. |
| Rotation | Rotates every dot. |
| Extra rotation where big | Dots turn more where the map is high. |
| Irregular outline | Wobbles the edge of each dot. |
| Fill | Solid dots, outlined rings, a mix that depends on size, or holes punched in a filled area. |
| Use rings below this size | For the mixed fill: the point where solid dots become rings. |
| Ring line thickness | Stroke width of rings. |

## Waves & bending (Distortion in Dots mode)

### Stripes

| Setting | Meaning |
|---|---|
| Waves · Strength | How far lines swing from side to side. |
| Number of waves | Waves along each line. In Rings this is rounded to a whole number so the circle closes cleanly. |
| Wave position | Slides the wave along the line. |
| Shift per stripe | Each next line starts its wave a little later. |
| Random bending · Strength, Detail | Irregular bending, like a melted print. |

### Dots

| Setting | Meaning |
|---|---|
| Liquid · Strength, Detail | Pushes dots out of the grid along a random flow. |
| Ripple · Strength, Number of ripples | Regular waves through the grid. |

## Color

| Setting | Meaning |
|---|---|
| Show background | Off makes the background transparent in the preview, SVG and PNG. |
| Background / Pattern | Pick a color or type a hex value. |
| Swap colors, B/W | Exchange the two colors, or reset to black on white. |
| Use a palette | One color, or several: one after another, random, by thickness, or as a smooth gradient. |
| Color order | Dots with a sequential palette: by row, column, diagonal or checker. |
| Gradient angle | Direction of the gradient. |
| Palette | Click a swatch to change it, **+** to add, the shuffle button to reorder, or pick a ready-made palette. |

## Effects

| Setting | Meaning |
|---|---|
| Draw outlines only | Stripes become outlines. **Line thickness** sets the stroke. |
| Melt | Blurs neighbouring shapes into each other. |
| Opacity | Transparency of the pattern. |
| Blend with background | How the pattern mixes with what is behind it. |

Melt and blend modes are exact in the browser and in PNG. Other applications may show the SVG differently.

## Second layer

Turns on a copy of the pattern drawn over the original. Small differences between the two create moiré.

| Setting | Meaning |
|---|---|
| Same colors as main pattern | Reuse the main colors, or give the copy its own color. |
| Rotate, Size, Move | Position of the copy. A few degrees of rotation is usually enough. |
| Blend with main pattern, Opacity | How the two layers mix. |

## Canvas

| Setting | Meaning |
|---|---|
| Width × height | Type a size in pixels (16 to 10,000). The lock keeps the proportions. |
| Presets | Common sizes for social posts, print and banners. |
| Swap orientation | Exchanges width and height. |
| Random seed | The same seed always gives the same random result. |

Very large canvases with many thin stripes or dense dots make the preview slower and the SVG larger.

## Saved patterns

Type a name and press **Save** to store the current settings with a thumbnail. Click a thumbnail to load it.

Saved patterns live in the browser's local storage. To keep them safe or move them to another device, use **Export JSON** and later **Import JSON**.
