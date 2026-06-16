# AutoStudio AI 🚗✨

**AI-powered automotive livery design studio — live at [nedkelly80.github.io/autostudio-ai](https://nedkelly80.github.io/autostudio-ai/)**

Upload any car photo, then:
- 🎨 **Change paint colour** — AI repaints the body while preserving all existing livery graphics, reflections, and background (ControlNet Canny, denoising 0.45)
- ✨ **Generate a new livery** — describe it in plain language and AI builds a complete racing livery while preserving the car's body shape (ControlNet Depth, denoising 0.78)
- 🖼 **Place logos** — drag, scale and rotate transparent PNGs on a Fabric.js canvas, then Bake with AI to integrate surface lighting and curvature (Inpainting, denoising 0.32)

## Quick start

```
# Open the studio
https://nedkelly80.github.io/autostudio-ai/

# Add a Fal.ai key for real AI (50 free gens/month)
⚙ Settings → Fal.ai API Key → paste key → Test → Save
```

## Features

| Feature | Tech | Detail |
|---------|------|--------|
| Paint colour change | ControlNet Canny | Locks all livery edge boundaries |
| Livery generation | ControlNet Depth | Preserves 3D car body shape |
| Logo bake | Inpainting | Integrates surface lighting |
| Before/after compare | Drag-handle slider | Visual A/B comparison |
| PDF spec sheet | Browser print API | Hand-off to print shop |
| PWA / offline | Service Worker | Installs as desktop/mobile app |
| TRM Racing presets | — | 6 Junior Sedan livery presets |

## Keyboard shortcuts

| Key | Action |
|-----|--------|
| `1` `2` `3` | Switch modes |
| `C` | Before/after compare |
| `M` | Toggle AI mask overlay |
| `⌘Z` | Reset to source |
| `⌘S` | Export image |
| `Del` | Delete selected logo |
| `?` | Shortcut panel |

## Architecture

```
Single HTML file (~62 KB)
├── Fabric.js 5.3 (CDN) — logo canvas
├── Fal.ai queue API — GPU inference with real-time polling
├── CSS variables — dark theme, mobile responsive
├── Service Worker — offline cache
└── PWA manifest — installable app
```

## AI provider setup

Get a key at [fal.ai](https://fal.ai) (free tier: 50 gens/month), paste it in ⚙ Settings. The app switches from mock canvas effects to real SDXL ControlNet inference.

**Endpoints used:**
- `queue.fal.run/fal-ai/controlnet-sdxl` — colour + livery
- `queue.fal.run/fal-ai/stable-diffusion-xl-v1-0/inpainting` — logo bake

## Local development

No build step needed — it's a single HTML file.

```bash
git clone https://github.com/Nedkelly80/autostudio-ai
cd autostudio-ai
npx serve .   # or just open index.html in a browser
```

Built by **TRM Racing Looms** · Darwin NT, Australia
