# ZimmCo Vending Unit

An interactive prop for the **ZimmCo Refreshment Vending Machine**, a module for the [Mothership RPG](https://www.tuesdayknightgames.com), written by Shane Vincent.

`index.html` is a self-contained page (styles, data, and script all inlined) — open it directly or drop it on any static host with no build step. The 3D view (see below) needs the page served over http(s) rather than opened as a `file://` URL.

## What it does

- **Coin-gated vending** — press the coin slot to arm the machine, then pick a flavour from the pad; only what the current unit's range actually stocks is selectable.
- **CRT-style display** with a durability gauge and a status light (green / flashing red in Lock Down).
- **Physics-driven can dispenser** — a vended can falls, bounces once out of the opening, and can be dragged around with the mouse before it's removed.
- **Latch mini-game** — clicking the small latch beside the coin slot climbs in pitch; the 10th press jams it, and pulls a random tool from the module's TOOLS table into a slide-out **Recovered Tools** panel.
- **Sound** — a synthesised coin-drop and latch clicks (Web Audio, no audio files needed); optional per-flavour voice lines drop into `audio/voices/` (see that folder's README).

## 3D view

The 3D view (`assets/vendingMachine.glb`, rendered with a locally vendored three.js — see `vendor/three/README.md`) is the default and only on-page view; there's no visible toggle. Drag to orbit, scroll to zoom.

Clicking the coin slot vends a random flavour from whatever the current unit stocks (same coin-drop sound and state as the classic machine, just without a specific flavour picked — see "Admin mode" for why). The `.glb` is a single merged mesh with no per-part names, so hit-testing works by comparing the raycast hit point against known world-space coordinates in the `HOTSPOTS` array instead of by mesh name.

A hidden `?classic` URL param (e.g. `http://localhost:4173/?classic`) shows the old DOM/CSS machine instead, for debugging state without the model loaded.

### Admin mode — capturing new hotspots

Since the model has no named parts, hotspot coordinates are captured by hand and hard-coded into `HOTSPOTS`. **Admin mode** (on by default on `localhost`; force with `?admin=1` / off with `?admin=0`) adds a capture tool for this, top-left, in **Chrome or Edge** (needs the File System Access API):

1. Click **Connect Hotspot Folder** and pick the repo's `hotspots/` directory.
2. Hold **left Ctrl** and click 4 points on the model to outline a zone. Every regular click also still logs its hit point to the console, if you just want a single coordinate.
3. On the 4th point, `hotspot-N.json` is written automatically (`N` auto-incremented) and a toast confirms it.
4. While Ctrl is held, every hotspot already in `HOTSPOTS` lights up pink on the model, so you can see what's already clickable.

See `hotspots/README.md` for the file format and the rest of the workflow (turning captured points into a real, named `HOTSPOTS` entry).

## Running locally

No build step — just serve the folder:

```bash
python -m http.server 4173
```

Then open `http://localhost:4173`.

## Hosting

Static site — works as-is on GitHub Pages, Netlify, Vercel, Cloudflare Pages, or any static file host that serves the repo over http(s) (needed for the 3D view's module scripts and model fetch). Point the host at `index.html` in the repo root.

## License

This product is based on the Mothership® Sci-Fi Horror Role Playing Game, published by Tuesday Knight Games. This product is published under license. MOTHERSHIP® is a registered trademark of Tuesday Knight Games. All rights reserved. For additional information, visit [tuesdayknightgames.com](https://www.tuesdayknightgames.com) or contact contact@tuesdayknightgames.com.
