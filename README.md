# ZimmCo Vending Unit

An interactive prop for the **ZimmCo Refreshment Vending Machine**, a module for the [Mothership RPG](https://www.tuesdayknightgames.com), written by Shane Vincent.

`index.html` is a self-contained page (styles, data, and script all inlined) — open it directly or drop it on any static host with no build step. The 3D view (see below) needs the page served over http(s) rather than opened as a `file://` URL.

## What it does

- **Coin-gated vending** — press the coin slot to arm the machine, then pick a flavour from the pad; only what the current unit's range actually stocks is selectable.
- **CRT-style display** with a durability gauge and a status light (green / flashing red in Lock Down).
- **Physics-driven can dispenser** — a vended can falls, bounces once out of the opening, and can be dragged around with the mouse before it's removed.
- **Latch mini-game** — clicking the small latch beside the coin slot climbs in pitch; the 10th press jams it, and pulls a random tool from the module's TOOLS table into a slide-out **Recovered Tools** panel.
- **Sound** — a synthesised coin-drop and latch clicks (Web Audio, no audio files needed); optional per-flavour voice lines drop into `audio/voices/` (see that folder's README).

## 3D view (proof of concept)

The **View** toggle in the top-left corner switches between the classic DOM/CSS machine and a work-in-progress 3D view (`assets/vendingMachine.glb`, rendered with a locally vendored three.js — see `vendor/three/README.md`). It defaults to the classic view.

Right now the 3D view proves the pipeline — load the model, orbit it, click a part and see which mesh got hit (logged to the console) — it isn't wired to the game logic yet. The current `.glb` is a single merged mesh, so every click reports the same object; splitting the model into separate named meshes per interactive part (coin slot, latch, each flavour button, ...) in Blender is the next step before individual clicks can drive `insertCoin()`, `pressLatch()`, `dispense(bev)`, etc.

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
