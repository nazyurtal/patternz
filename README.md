# patternz

A browser-based generator for op-art patterns: stripes that swell and taper, concentric rings, rays, halftone dot grids and moiré overlays. Everything is drawn as vector shapes, so you can export clean SVG as well as PNG.

![patternz screenshot](docs/screenshot.png)

patternz is a single HTML file. There is no build step, no server and no dependencies to install.

## Features

- **Two pattern types**: stripes (vertical, horizontal, rings, rays) and dots (square, honeycomb or circular grid).
- **Thickness map**: ten ways to decide where the pattern is thick and where it is thin, including waves, gradients, ripples, spirals, random clouds and a single band.
- **Pieces**: cut each stripe into segments and taper them into lenses, wedges or hourglasses.
- **Distortion**: waves, random bending, liquid displacement and ripples.
- **Color**: background and pattern color with hex input, palettes (in sequence, random, by thickness, or as a gradient) and a transparent background option.
- **Second layer**: a rotated, scaled or shifted copy on top for moiré interference.
- **Variations**: a grid of alternatives generated around the current pattern, at three strengths.
- **Direct manipulation**: drag on the canvas to move the center of circular layouts.
- **Undo and redo**, a saved-pattern library with thumbnails, and settings import/export as JSON.
- **Export**: SVG, flattened SVG, PNG at 1×, 2× and 4×, and copy to clipboard as SVG or PNG.
- **Responsive**: works on desktop, tablet and phone.

## Getting started

Download or clone the repository and open `index.html` in a browser.

```bash
git clone https://github.com/<your-username>/patternz.git
cd patternz
open index.html        # macOS; on Windows or Linux, double-click the file
```

Copying a PNG to the clipboard needs a secure context. If that button does nothing when the file is opened directly, serve the folder locally instead:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

The interface loads the Inter typeface from Google Fonts and falls back to the system font when offline.

## Publishing with GitHub Pages

1. Push the repository to GitHub.
2. Open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, then select `main` and `/ (root)`.
4. Save. The site appears at `https://<your-username>.github.io/patternz/` after a minute or two.

## Keyboard shortcuts

| Key | Action |
|---|---|
| `R` | Randomize |
| `V` | Open variations |
| `S` | New random seed |
| `B` | Toggle background |
| `F` | Focus mode (hide the settings panel) |
| `?` | Show shortcuts |
| `Ctrl/⌘ + Z` | Undo |
| `Ctrl/⌘ + Shift + Z` | Redo |
| `Esc` | Close menus and dialogs |

Double-click a setting's label to reset it. Each group also has its own **Reset** link.

## Export formats

| Format | Use it when | Notes |
|---|---|---|
| **SVG** | You want to keep editing in Illustrator, Figma or similar | Every stripe and dot is its own path, clipped to the canvas, with no masks or transforms. |
| **SVG · exact look** | You need the result to look identical everywhere | Contains a high-resolution image, so it is not editable as vector. |
| **PNG 1× / 2× / 4×** | You need a raster image | Transparent when the background is off. |
| **Copy SVG / PNG** | You want to paste straight into another app | PNG copy depends on browser clipboard support. |

Two effects cannot be stored as plain vector shapes: **Melt** and **blend modes**. Browsers render them correctly, but other applications may show them differently or ignore them. The export menu warns you when one of them is active; use PNG or *SVG · exact look* in that case.

## Documentation

- [User guide](docs/USER_GUIDE.md): every setting, explained.
- [Development notes](docs/DEVELOPMENT.md): how the code is organized and how to extend it.
- [Changelog](CHANGELOG.md)
- [Contributing](CONTRIBUTING.md)

## Browser support

Current versions of Chrome, Edge, Firefox and Safari. Saved patterns and the last session are kept in the browser's local storage, so they stay on the device and browser where they were created.

## License

No license has been chosen yet. Until one is added, the code is not licensed for reuse by others. If you want this to be open source, add a `LICENSE` file (see [choosealicense.com](https://choosealicense.com)).
