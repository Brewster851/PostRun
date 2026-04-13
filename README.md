# runlog.gg

A tactical board for breaking down Marathon runs with your squad.

Take a screenshot of the in-game map after a memorable run, then mark up enemy positions, your team's movement, kills, downs, loot, and extractions across multiple frames in time. Export individual frames as PNGs to drop in Discord, or zip up the whole run.

Built specifically for Bungie's Marathon (2026), with the four launch maps (Perimeter, Dire Marsh, Outpost, Cryo Archive) baked in. You can also upload your own screenshots for any map.

## Features

- **Built-in maps** — Perimeter, Dire Marsh, Outpost, Cryo Archive ready to go
- **Custom backgrounds** — upload any screenshot to use as a base
- **Timeline frames** — multiple snapshots per run, one per moment, to show movement over time
- **Stamps** — ally runners, enemy teams, UESC AI, kills, downs, revives, firefights, loot, extracts, cores, POIs
- **Drawing tools** — freehand, lines, arrows, text labels
- **Selection** — click to select stamps, text, or strokes; drag to marquee multiple; resize, recolor, move, or delete
- **Pan & zoom** — scroll to zoom toward your cursor, hold space to pan, all annotations stay pixel-sharp at any zoom
- **Local saves** — runs are stored in browser localStorage, accessible across sessions
- **Export** — single frame as PNG, or all frames zipped together

## Running locally

This is a static site with no build step. To run it:

1. Open `index.html` directly in a browser, or
2. Serve the folder with any static file server, e.g.:
   ```
   python3 -m http.server 8000
   ```
   then visit `http://localhost:8000`

The map PNGs need to be in the same folder as `index.html`.

## Hosting

Push the repo to any static host. Cloudflare Pages, GitHub Pages, Netlify, and Vercel all work with zero configuration — just point them at this repo and they'll serve `index.html` at the root.

## Files

- `index.html` — the entire app (HTML, CSS, JS in one file)
- `perimeter.png` / `dire_marsh.png` / `outpost.png` / `cryo_archive.png` — map backgrounds, loaded on demand
- `jszip.min.js` — bundled dependency for ZIP export
- `favicon.svg` / `favicon.ico` — browser tab icon

## Tech

Pure vanilla HTML, CSS, and JavaScript. No framework, no build step. The only dependency is JSZip 3.10.1 (used for the "Export All Frames" feature), bundled directly in the repo as `jszip.min.js` rather than loaded from a CDN — no external requests at runtime.

Saved runs live in `localStorage` under the key `marathon_tac_runs_v1`. They don't sync between users or devices — clearing browser data wipes them.

## Caveats

- Map screenshots have a finite resolution; zooming way past native will show pixelation in the background (annotations stay sharp)
- localStorage caps around 5–10MB per origin, so very large user-uploaded screenshots eat into the saved-run budget faster than the built-in maps

## Disclaimer

Not affiliated with, endorsed by, or sponsored by Bungie, Inc. Marathon, the Marathon logo, map names (Perimeter, Dire Marsh, Outpost, Cryo Archive), and game content are trademarks and copyrighted works of Bungie. This is an independent fan project for planning and reviewing runs with friends. If you're from Bungie and would like any content removed, please open an issue on the repo.
