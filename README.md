# ZimmCo Vending Unit

An interactive prop and GM reference for the **ZimmCo Refreshment Vending Machine**, a module for the [Mothership RPG](https://www.tuesdayknightgames.com), written by Shane Vincent.

Single self-contained page — `index.html` has everything inlined (styles, data, script), so it can be opened directly or dropped on any static host with no build step.

## What it does

- **Cabinet console** — roll up a machine (Durability, stock, flavour range), vend a random can or pick one from the pad, and track Opened / Hacked / Lock Down state as play happens.
- **Beverage catalog** — all eight flavours with their effects.
- **Rumor terminal** — d10 roll on the first-encounter rumor table.
- **Machine states** — Opened / Hacked / Lock Down reference.
- **Alternate actions** — expandable reference for Crack It Open, Hack the Mainframe, Tools (with its own drawer roll), Terminal, Transceiver, Proximity Sensor, Shelter, Jump Start, Lifesaver, and Fizzler.
- **Merch crate** — pull a random piece of ZimmCo ephemera.

## Running locally

No build step — just serve the folder:

```bash
python -m http.server 4173
```

Then open `http://localhost:4173`.

## Hosting

Static single-file site — works as-is on GitHub Pages, Netlify, Vercel, Cloudflare Pages, or any static file host. Point the host at `index.html` in the repo root.

## License

This product is based on the Mothership® Sci-Fi Horror Role Playing Game, published by Tuesday Knight Games. This product is published under license. MOTHERSHIP® is a registered trademark of Tuesday Knight Games. All rights reserved. For additional information, visit [tuesdayknightgames.com](https://www.tuesdayknightgames.com) or contact contact@tuesdayknightgames.com.
