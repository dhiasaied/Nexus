# NEXUS Humanoid Robotics

A static multi-page marketing website for **NEXUS**, a fictional humanoid robotics brand. The site presents product storytelling, interactive 3D visuals, a technology overview, a demo hardware shop, and simulated authentication flows — all client-side, with no backend.

> *“Autonomous bipedal intelligence engineered for industrial scale, physical endurance, and seamless human coexistence.”*

---

## Features

### Home (`index.html`)
- Full-bleed hero with an interactive **Three.js** procedural humanoid
- Live-style telemetry HUD (battery, neural sync, payload, DoF)
- Chassis variant switcher: **NEXUS PRIME**, **APEX**, and **CORE**
- Spec highlights, autonomy features, and enterprise pilot CTA (UI only)
- Scroll-reveal animations and shared site navigation

### Robots (`Robot.html`)
- **3D Telemetry Inspection Dock** with modes: Rotate 360°, X-Ray, Torque, Thermal
- Fleet lineup: **Prime Gen-3** (28 DoF), **Core Lite** (24 DoF), **Apex Pro**
- Comparative specification matrix (torque, sensors, battery, SDK, TOPS, tactile sensitivity)

### Technology (`technology.html`)
- Six technology pillars: AI, Computer Vision, Motion Planning, Sensors & Haptics, Autonomous Navigation, ML & Fleet Simulation
- Actuator showcases and telemetry gauge UI
- Open NEXUS SDK section with tabbed illustrative code (Python / ROS2 / C++)

### Shop (`Shop.html`)
- Product catalog with search, category filters, and price slider
- Currency switcher: **TND / EUR / BTC** (client-side conversion; prices in Tunisian dinars)
- In-memory shopping cart (quantity controls and subtotal; not persisted)
- Catalog includes robots, actuators, docks, and merchandise

### Authentication (simulated)
- `login.html` — sign-in UI with password toggle and demo SSO / FIDO2 buttons
- `register.html` — registration with password strength meter and match checks
- `forgot_password.html` / `reset_password.html` — password recovery and reset flows

> **Note:** Cart, auth, SSO/FIDO2, SDK download, and enterprise forms are front-end simulations. There is no server, database, payment processor, or real SDK package.

---

## Project structure

```
humanoid_robotics_platform/
├── index.html                 # Landing page
├── Robot.html                 # Fleet & 3D inspection
├── technology.html            # Technology pillars & SDK showcase
├── Shop.html                  # Hardware store & cart
├── login.html                 # Login demo
├── register.html              # Registration demo
├── forgot_password.html       # Forgot password demo
├── reset_password.html        # Reset password demo
└── assets/
    ├── css/
    │   └── animations.css     # Shared motion, tokens, reduced-motion
    └── img/
        ├── nexus-logo.svg     # Brand mark
        └── nexus-tactical-cyber-jacket.jpg
```

---

## Tech stack

| Layer | Technology |
|--------|------------|
| Markup | HTML5 (static multi-page site) |
| Styling | [Tailwind CSS](https://tailwindcss.com) via CDN |
| Theme | Per-page inline `tailwind.config` (dark industrial palette, primary cyan `#00f0ff`) |
| Fonts | [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk), [Manrope](https://fonts.google.com/specimen/Manrope), [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) |
| Icons | [Material Symbols Outlined](https://fonts.google.com/icons) |
| 3D | [Three.js](https://threejs.org) **r125** |
| Motion | Custom CSS (`assets/css/animations.css`) |
| Logic | Vanilla JavaScript (inline page scripts) |

No package manager, bundler, Docker setup, or server-side runtime is required. Dependencies load from CDNs at runtime.

---

## Requirements

- A modern browser with WebGL support (for Three.js scenes)
- Network access for CDN assets (Tailwind, Three.js, Google Fonts, remote product images)
- Optional: Python 3 or Node.js to serve the site over HTTP locally

---

## Installation

There are no npm or pip packages to install. Clone or copy the project folder:

```bash
cd humanoid_robotics_platform
```

---

## Configuration

This project has **no** `.env` files, environment variables, or external config files.

Design and behavior are controlled by:

| Item | Location |
|------|----------|
| Color / typography tokens | Inline `tailwind.config` in each HTML page |
| Motion & CSS variables (`--nx-cyan`, easings) | `assets/css/animations.css` |
| Dark mode | `<html class="dark">` with Tailwind `darkMode: "class"` |
| Brand assets | `assets/img/` |

To change the visual theme, edit the shared Tailwind config blocks and/or `animations.css`. Keep the same tokens across pages for a consistent look.

---

## Usage

Serve the folder over HTTP (recommended over opening files via `file://`):

**Python**

```bash
python -m http.server 8080
```

**Node.js**

```bash
npx --yes serve .
```

Then open:

| Page | URL |
|------|-----|
| Home | http://localhost:8080/index.html |
| Robots | http://localhost:8080/Robot.html |
| Technology | http://localhost:8080/technology.html |
| Shop | http://localhost:8080/Shop.html |
| Login | http://localhost:8080/login.html |

### Typical flows

1. **Explore the brand** — start on Home; switch chassis variants and scroll through autonomy / applications sections.
2. **Inspect the fleet** — open Robots; use the inspection dock mode buttons and compare models in the matrix.
3. **Browse technology** — open Technology; switch SDK language tabs for illustrative snippets.
4. **Demo the store** — open Shop; filter products, change currency, add items to the cart drawer.
5. **Try auth UI** — walk through Login → Register → Forgot / Reset password screens (client validation only).

---

## Browser & accessibility notes

- `assets/css/animations.css` respects `prefers-reduced-motion: reduce`
- Fixed header anchors use `scroll-margin-top` for in-page sections (`#about`, `#applications`, and others)
- Three.js canvases require WebGL; scenes degrade if the GPU context is unavailable
