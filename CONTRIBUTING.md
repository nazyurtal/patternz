# Contributing

Thanks for your interest in patternz.

## Reporting a problem

Open an issue and include:

- What you did and what you expected.
- Browser and operating system.
- The pattern's settings: open **Saved patterns → Export JSON** and paste the text. This lets anyone reproduce the exact pattern.
- For export problems, the application you opened the file in and a screenshot.

## Making a change

1. Fork the repository and create a branch.
2. Edit `index.html`. There is no build step; reload the browser to see changes.
3. Read [docs/DEVELOPMENT.md](docs/DEVELOPMENT.md) for the structure of the code and for how to add a setting.
4. Before opening a pull request, check that:
   - the page loads without console errors in both Stripes and Dots mode,
   - Randomize, Variations, Undo and Export still work,
   - the layout holds at phone width (around 375 px),
   - exported SVGs contain no clip paths, masks or transforms.
5. Describe what changed and why in the pull request, and add a line to `CHANGELOG.md`.

## Style

- Keep the project a single dependency-free HTML file.
- Interface text is in English, in plain language. Prefer "Thinnest" over "Min width".
- New settings need a default in `DEF`, a control in `SCHEMA` and a label in `LBL`.
