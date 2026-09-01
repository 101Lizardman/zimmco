# ZimmCo Vending Unit — Development Notes

This is the technical README — architecture, local dev, and hosting. Looking for how to actually run this at the table? See [`README.md`](README.md).

`index.html` is a self-contained page (styles, data, and script all inlined) — open it directly or drop it on any static host with no build step. The 3D view (see below) needs the page served over http(s) rather than opened as a `file://` URL.

## What it does

- **Coin-gated vending** — press the coin slot to arm the machine, then pick a flavour from the pad; only what the current unit's range actually stocks is selectable.
- **CRT-style display** with a durability gauge and a status light (green idle / fast red blink in Lock Down / solid steel blue while Hacked).
- **Physics-driven can dispenser** — a vended can falls, bounces once out of the opening, and can be dragged around with the mouse before it's removed.
- **Latch mini-game** — clicking the small latch beside the coin slot climbs in pitch; the 15th press jams it, and pulls a random tool from the module's TOOLS table into a slide-out **Recovered Tools** panel.
- **Alternate-action hotspots** — Hack the Mainframe, Crack It Open (x2, one per side panel), and Proximity Sensor are all real clickable points on the 3D model, each gated behind a click count and (except Crack It Open) an INTELLECT stat check.
- **Hacked / Internals side panels** — password-gated tiles (Terminal / Transceiver / Shelter / Jump Start) that unlock once the machine is Hacked or Opened respectively; see the main README for the actual passwords and their in-fiction rumors.
- **Lock Down** — red alarm light, a repeating alarm SFX, the scene's key light turning red, and a ZAP! BODY-save modal gating every action on the machine (one click instead of the usual click-gate once locked down).
- **Sound** — entirely synthesised via the Web Audio API (coin drop, latch clicks, hack buzz, thunk/metal crunch, metal bend, steam hiss, alarm, ZAP) plus a few real sfx/voice-line assets under `assets/sfx/` and `audio/voices/`.

## 3D view

The 3D view (`assets/vendingMachine.glb`, rendered with a locally vendored three.js — see `vendor/three/README.md`) is the default and only on-page view; there's no visible toggle. Drag to orbit, scroll to zoom.

Clicking the coin slot vends a random flavour from whatever the current unit stocks. The `.glb` is a single merged mesh with no per-part names, so hit-testing works by comparing the raycast hit point against known world-space coordinates in the `HOTSPOTS` array instead of by mesh name.

A hidden `?classic` URL param (e.g. `http://localhost:4173/?classic`) shows the old DOM/CSS machine instead, for debugging state without the model loaded.

### Cache-busting

Every asset URL (sfx, voice lines, both `.glb` models, the loading-screen logo) gets a `?v=<page-load timestamp>` query string appended at runtime. Without it, replacing a file on disk doesn't show up until a hard refresh, since the browser (and GitHub Pages' CDN) cache by URL and nothing about the URL itself changes when the file's contents do.

### Admin mode — capturing new hotspots, forcing states

Since the model has no named parts, hotspot coordinates are captured by hand and hard-coded into `HOTSPOTS`. **Admin mode** (on by default on `localhost`; force with `?admin=1` / off with `?admin=0`) adds a panel for this, top-left:

1. Click **Connect Hotspot Folder** and pick the repo's `hotspots/` directory (**Chrome or Edge** only — needs the File System Access API).
2. Hold **left Ctrl** and click 4 points on the model to outline a zone. Every regular click also still logs its hit point to the console, if you just want a single coordinate.
3. On the 4th point, `hotspot-N.json` is written automatically (`N` auto-incremented) and a toast confirms it.
4. While Ctrl is held, every hotspot already in `HOTSPOTS` lights up pink on the model, so you can see what's already clickable.

See `hotspots/README.md` for the file format and the rest of the workflow (turning captured points into a real, named `HOTSPOTS` entry).

The same panel has a **Force Machine State** row (Operational / Opened / Hacked / Lock Down) for jumping straight to a state while testing, without grinding through the actual rolls — more than one can show active at once, since Hacked and Opened are sticky and don't clear when Lock Down toggles on top of them.

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
