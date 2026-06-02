# Architecture & Design Decisions

## Tech Stack
| Layer | Technology | Reason |
|---|---|---|
| Framework | Vanilla HTML/CSS/JS | Zero build step, runs on any static server |
| 3D Map | Three.js r128 (CDN) | Best-in-class WebGL 3D rendering |
| 3D Camera | Three.js (same instance) | Consistent rendering pipeline |
| Styling | Pure CSS with variables | No framework needed, full control |

## Architecture
```
index.html
├── CSS (inline) — layout, components, animations
├── Three.js Scene 1 — 3D Map (point cloud floor plan)
│   ├── Floor plane (white)
│   ├── Wall meshes (BoxGeometry)
│   ├── Pink restricted zones (PlaneGeometry)
│   ├── LiDAR scan points (Points + BufferGeometry)
│   ├── Red artifact points
│   └── Robot (Group: body + wheels + antenna + dome)
├── Three.js Scene 2 — Camera Feed (warehouse)
│   ├── Floor + walls
│   ├── Safety fence (yellow)
│   └── Boxes/pallets
└── JS Logic
    ├── Mission state (running/paused)
    ├── AUTO/MANUAL mode
    ├── Battery drain simulation
    ├── Robot autonomous movement
    ├── Keyboard controls (WASD/Arrows/Space)
    └── Toast notifications
```

## Key Design Decisions

### Single HTML file
- No build tools required
- Runs instantly on any static server
- Easy to review and grade

### Three.js for both map AND camera
- 3D map matches reference GIF — tilted perspective with point cloud dots
- Camera shows realistic warehouse scene (not a static image)
- Both scenes render at 60fps

### Robot simulation
- In AUTO mode: robot navigates autonomously with smooth interpolation
- In MANUAL mode: WASD/D-pad/arrow key control
- Robot rotates to face direction of travel

### Extending for production
- Swap Three.js map with real PCD file using PCDLoader
- Replace camera canvas with video stream
- Add ROSLib.js for real robot telemetry
