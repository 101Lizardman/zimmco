# Captured hotspots

Output of the in-page **admin hotspot capture tool** (see `vendor/three/README.md` for the 3D view it's part of, and the "Admin mode" section of the main `README.md`).

## Workflow

1. Run the site locally (`python -m http.server` from the repo root) and open it in **Chrome or Edge** — the capture tool needs the File System Access API, which only those support. Admin mode is on by default on `localhost`.
2. Click **Connect Hotspot Folder** (top-left panel) and pick *this* `hotspots/` directory.
3. Hold **left Ctrl** and click 4 points on the model to outline a zone — a small marker drops at each point, and the panel counts you up (1/4 → 4/4).
4. On the 4th point, a file is written here automatically — `hotspot-N.json`, `N` auto-incremented from whatever's already in this folder — and a toast confirms the number.
5. Repeat for every part you want clickable (coin slot, latch, each flavour button, ...).

## File format

```json
{
  "id": 1,
  "points": [
    { "x": 0, "y": 0, "z": 0 },
    { "x": 0, "y": 0, "z": 0 },
    { "x": 0, "y": 0, "z": 0 },
    { "x": 0, "y": 0, "z": 0 }
  ],
  "createdAt": "2026-08-31T12:00:00.000Z"
}
```

`points` are world-space coordinates on the model's surface (same space the console already logs for every 3D click), in the order you clicked them.

## Next step

These files are just the raw capture — nothing reads them at runtime yet. Once you know which number is which part (open a couple in a text editor, or just remember the click order), say so and the actual `HOTSPOTS` array in `index.html` gets built from these points, wired to real actions.
