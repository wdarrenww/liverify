# Liverify

A high-performance, cross-platform livery editor tailored specifically for creating and managing custom vehicle liveries in **Emergency Response: Liberty County (Roblox)**.

Designed for intelligent, reusable, and scalable workflows across multiple vehicle templates, with full support for **vector + raster** editing, flip-safe design logic, and batch export for Roblox deployment.

---

## Key Features

### General Image Editing

- Layer-based editor (create, reorder, hide, lock, delete)
- Vector support: shapes, text, scalable logos
- Raster tools: freehand brush, image import, eraser
- Transform tools: move, scale, rotate, mirror (with exclusions)
- Undo/redo with full history
- Canvas tools: zoom, pan, snapping, grid

---

### ER:LC-Specific Capabilities

- Overlay support for ER:LC UV vehicle templates
- Define & edit **meta-zones** (door, hood, rear) mapped across vehicles
- Flip/mirror a full design without flipping text or badges
- Design once → apply to multiple vehicle templates automatically
- Export correctly sized **Roblox-ready PNGs**
- Vehicle-specific configs (zones, template image, export resolution)
- Constraints checker for Roblox upload: max resolution, file size, aspect ratio

---

### Advanced/Optional Features (Planned)

- Template importer and zone mapper (custom template creation)
- 3D vehicle preview (UV-mapped mesh + livery wrap)
- Asset library (logos, fonts, saved shapes)
- Project save/load with editable `.elcproj` format
- Cross-platform: Windows, macOS, Linux
- Template sharing/export via `.elcwrap` bundle format

---

## Roadmap

### Phase 1: Core Editor
- [ ] Layered canvas editor (Konva.js / Pixi.js)
- [ ] Text and vector shape tools
- [ ] Image import, transform, and export
- [ ] PNG export @ fixed resolution
- [ ] Rust backend with image processing (via WASM)

### Phase 2: ER:LC Specific Logic
- [ ] Vehicle template overlays
- [ ] Design zones (e.g., `hood`, `door`, etc.)
- [ ] Flip-safe layer logic
- [ ] Cross-vehicle propagation using shared zones
- [ ] Reference image displayed on the side for convenience.

### Phase 3: Export & Constraints
- [ ] Batch export across multiple vehicles
- [ ] Export naming conventions
- [ ] File size/resolution checker for Roblox
- [ ] Export wizard

### 🔭 Phase 4: Extras
- [ ] 3D vehicle preview (Three.js or Bevy)
- [ ] Template importer/editor (with zone def)
- [ ] Asset packs and reusable elements
- [ ] Online template repository
- [ ] AI mapping from reference images to the vehicle

---

## Technologies

| Component | Stack |
|----------|-------|
| Image Core | `Rust` + `image`, `resvg`, `wasm-bindgen` |
| Frontend | `React`, `TypeScript`, `Konva.js` or `PixiJS` |
| Native Shell | `Tauri` |
| Storage | Local filesystem + `serde_json` project files |
| Build | `Vite` + `Cargo` |
| Future 3D | `Three.js` or `Bevy` (for preview) |

---

## Project Format (`.elcproj`)

All projects are saved in JSON:

```json
{
  "canvas": { "width": 1024, "height": 1024 },
  "layers": [
    {
      "name": "Base Shape",
      "type": "vector",
      "flip_safe": true,
      "elements": [ ... ]
    }
  ],
  "vehicles": ["2020 Explorer", "Dodge Charger"],
  "zones": {
    "door": [[0.1, 0.2], [0.3, 0.5]],
    "hood": [[0.2, 0.7], [0.4, 0.9]]
  }
}
```

---

## Dev Setup
```bash
# 1. Clone and install dependencies
git clone https://github.com/your-username/elc-livery-editor
cd elc-livery-editor
npm install

# 2. Build the WASM module
cd backend
wasm-pack build --target web

# 3. Run the app
cd ../frontend
npm run dev
```

To run as a desktop app:

```bash
npm run tauri dev
```

---

## Folder Structure
```bash
liverify/src/
├── backend/           # Rust core (WASM image engine)
├── frontend/          # React + Konva editor UI
├── templates/         # Vehicle template overlays + zone configs
├── projects/          # Saved .elcproj files
├── assets/            # Logos, font packs, etc.
├── tauri.conf.json    # Native app config
└── README.md
```

---

## FAQ

Q: Can I use this for other Roblox games?
A: Technically yes, but it's built around ER:LC’s vehicle template structure.

Q: Can I define my own vehicle templates?
A: Yes, a zone-based template editor is part of the roadmap (Phase 4).

---

## Contributors

- wwdarrenw

---

## License

MIT License. See LICENSE for details.

