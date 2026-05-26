# Stage Hop · 春声

**Unofficial fan guide to Primavera Sound Barcelona 2026**

[![Live Demo](https://img.shields.io/badge/demo-stagehop.live-4a90d9?style=flat-square)](https://stagehop.live/)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)
[![Vanilla JS](https://img.shields.io/badge/built%20with-Vanilla%20JS-f0db4f?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![PWA](https://img.shields.io/badge/PWA-installable-7c3aed?style=flat-square)](https://stagehop.live/)

---

## Screenshots

*Screenshots coming soon.*

---

## Features

- **Full lineup schedule** — browse all five days with time, stage, and headliner info
- **Clash detection** — favorite any artist and instantly see which shows conflict
- **Interactive venue map** — tap a stage hotspot to see what's playing there and when
- **Multilingual** — full UI and practical info in English, Spanish, and 中文
- **Installable PWA** — add to your home screen and use it without a connection
- **Sort & filter** — by time, artist name, or your saved favorites
- **Practical info** — transport, tips, prohibited items, and live weather forecast
- No signup. No ads. No tracking beyond anonymous performance metrics.

---

## Why I built this

The festival's official app is fine, but it doesn't handle clashes well, has no Chinese interface, and isn't great on slow mobile data. I have friends coming from China and Taiwan who wanted something they could read in their language and trust to work when the wifi at Parc del Fòrum is, predictably, a disaster. So I spent a few evenings building exactly that.

---

## Tech

**Stack:** plain HTML, CSS, and vanilla JavaScript. No React, no Vue, no build step, no node_modules.

**Deployed on:** [Vercel](https://stagehop.live/) (primary) and [GitHub Pages](https://max7770101.github.io/stagehop.live/) (mirror)

**PWA:** `manifest.json` for home screen installability on iOS and Android

**Why no framework:** the project is five festival days of static data and a handful of UI interactions. A framework would add more complexity than it removes, and would make the bundle bigger on the exact network conditions where you want it to load fast — standing outside a stage trying to check what's on next.

**Icons:** generated with PowerShell + `System.Drawing` (no Node, no ImageMagick)

---

## Local development

No setup required. Just open `index.html` in a browser:

```bash
git clone https://github.com/MAX7770101/stagehop.live.git
cd stagehop.live
open index.html   # macOS
# or: start index.html  (Windows)
# or: xdg-open index.html  (Linux)
```

For features that need a server context (manifest, some PWA behaviour), use any static server:

```bash
npx serve .
# or: python -m http.server 8080
```

### File structure

```
index.html          — app shell, navigation, all four view containers
styles.css          — theming via CSS custom properties
src/
  data.js           — all festival data (stages, shows)
  localization.js   — UI strings in zh / es / en
  scripts.js        — all UI logic (views, favorites, map, timers)
assets/
  favicon.ico / *.png   — PWA icons and favicons
  og-image.png          — social share preview image
  map.jfif              — venue map image
scripts/
  generate-icons.ps1    — regenerates all icon assets (Windows / PowerShell)
manifest.json       — PWA manifest
robots.txt
```

### Simulation mode

`scripts.js` has a `SIM_ENABLED` flag near the top. Set it to `true` to test the now-playing and clash features at any simulated time without waiting for the actual festival dates.

---

## Disclaimer

This is a fan-made project. It is **not affiliated with, endorsed by, or connected to Primavera Sound S.L.** in any way.

All trademarks, artist names, and festival branding belong to their respective owners. Schedule data is compiled from publicly available sources and may contain errors or omissions — always verify times on the [official Primavera Sound website](https://www.primaverasound.com) before heading to a stage.

---

## Contributing

Bug reports, corrections, and feedback are welcome via [GitHub Issues](https://github.com/MAX7770101/stagehop.live/issues).

For anything else: **maxx7770101@gmail.com**

---

## License

[MIT](LICENSE) — do whatever you want with the code, just don't pass it off as an official Primavera Sound product.

---

## Acknowledgments

[Clashfinder](https://clashfinder.com/) was a big inspiration for the approach — prove that a simple, focused tool beats a bloated app for this use case. Thanks to the friends who tested it in the lead-up and caught things I'd stopped noticing.
