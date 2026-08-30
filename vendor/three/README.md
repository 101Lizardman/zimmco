# Vendored three.js

Three.js is vendored locally (not loaded from a CDN) so the site has no external script dependency and works the same whether it's opened straight from disk over a local server, deployed to GitHub Pages, or previewed elsewhere.

- **Version**: 0.160.0
- **Source**: https://unpkg.com/three@0.160.0/ (mirrors the npm package's own directory layout, so the addon modules' internal relative imports resolve unmodified)
- **License**: MIT — see the header comment in `build/three.module.js`

Files:

```
vendor/three/
  build/three.module.js                        core library
  examples/jsm/loaders/GLTFLoader.js            .glb/.gltf model loader
  examples/jsm/controls/OrbitControls.js        mouse/touch orbit camera
  examples/jsm/utils/BufferGeometryUtils.js     GLTFLoader's own dependency
```

`index.html` resolves the bare `import * as THREE from "three"` specifier used inside the addon files via an import map — see the `<script type="importmap">` block.

To upgrade: replace these four files with the same version pulled from `https://unpkg.com/three@<version>/...` at the same relative paths, and update the version above.
