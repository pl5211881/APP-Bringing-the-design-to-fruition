# Project Guide

## Current Project Shape

- Root files: `index.html`, `styles.css`, `README.md`, `.nojekyll`, `.gitignore`.
- Runtime assets: `assets/` contains required SVG, PNG, WebM, and MOV files.
- The page is currently a no-build static prototype. Local preview command:

```bash
python3 -m http.server 4174
```

- GitHub remote used in this project:

```text
git@github.com:pl5211881/APP-Bringing-the-design-to-fruition.git
```

## Core UI Concepts

- The `.phone-screen` keeps a 414px design coordinate system and scales via `--phone-scale`.
- The primary flow is one page with multiple states, not separate HTML pages:
  - `idle`: ungenerated AI learning report card.
  - `generating`: step-by-step generation process.
  - `done`: generated report card with expandable thinking process.
  - `detail`: quality detection result page.
- `phone.dataset.view` and `phone.dataset.reportState` control visible page/state.
- Assets are referenced with relative paths such as `./assets/...` to remain GitHub Pages-compatible.

## Bottom Dock Rules

- The bottom button and touchbar live in `.bottom-dock`.
- Use CSS sticky for stable bottom behavior:
  - `.bottom-dock { position: sticky; bottom: 0; }`
  - Do not move the dock on scroll with JS using `scrollTop`.
- Keep the button/touchbar gap through variables:
  - `--cta-height`
  - `--touchbar-height`
  - `--cta-touchbar-gap`
  - `--bottom-dock-height`
- `scroll-spacer` exists to give content enough scrollable height without creating infinite empty scroll.

## Dynamicization Path

When converting this into a dynamic app:

1. Extract static content into a data object:
   - student summary
   - metrics
   - generation steps
   - weak knowledge cards
   - review path cards
2. Keep existing visual classes and map data into DOM or component templates.
3. Preserve the flow contract:
   - click generate
   - step progress from first item to last item
   - only show generated card after all steps are completed
   - generated thinking expansion shows completed static steps
   - detail page opens from the generated CTA
4. If migrating to React/Vue/Vite, keep assets under a public/static asset path and verify video playback after build.

## Validation Checklist

- `index.html` and `styles.css` brace-depth check passes.
- Local server opens without missing asset 404s other than optional favicon.
- Short states do not scroll into blank space.
- Long states scroll only until content plus bottom dock is visible.
- Bottom CTA and touchbar do not jitter during inertial scroll.
- Git status is clean or only contains intentional untracked files before push.

