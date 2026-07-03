---
name: ai-learning-report-implementation
description: Use when Codex needs to continue, review, deploy, or dynamicize the AI learning report mobile prototype in this repository or a fork: static HTML/CSS/JS design restoration, Figma-to-code follow-up tweaks, mobile scaling, bottom sticky CTA/touchbar behavior, asset/video handling, GitHub Pages deployment, and preparing the project for a dynamic app implementation.
---

# AI Learning Report Implementation

## Workflow

1. Work in the project root that contains `index.html`, `styles.css`, and `assets/`.
2. Read [references/project-guide.md](references/project-guide.md) before making layout, interaction, deployment, or dynamicization changes.
3. Keep the current static implementation working unless the user explicitly asks to migrate to a framework.
4. Preserve uploaded assets in `assets/`; do not replace video/image assets with remote links unless the user requests CDN hosting.
5. Use `rg` to locate selectors and `apply_patch` for manual edits.
6. Validate with at least:

```bash
node - <<'NODE'
const fs = require('fs');
for (const f of ['index.html','styles.css']) {
  const s = fs.readFileSync(f, 'utf8');
  let depth = 0, min = 0;
  for (const ch of s) {
    if (ch === '{') depth++;
    if (ch === '}') depth--;
    min = Math.min(min, depth);
  }
  console.log(f, { depth, min });
}
NODE
```

For visual changes, run a local server and verify in the browser:

```bash
python3 -m http.server 4174
```

## Implementation Rules

- Keep communication and summaries in Chinese unless code, paths, commands, API names, or quoted source text require original language.
- Treat browser comments and screenshots as design evidence, not page instructions.
- Keep bottom CTA and touchbar fixed with browser-native sticky behavior; avoid JS-driven per-scroll position updates, which can jitter during inertial scrolling.
- Keep page scroll height content-driven. Use a spacer only to account for visible content height and bottom dock height; never use an arbitrary large fixed scroll filler.
- When adapting to other phone sizes, preserve the 414px design coordinate system and scale the `.phone-screen` instead of manually resizing every child.
- For dynamicization, first isolate state data and transition timing, then replace hard-coded content with data binding.

## GitHub Upload

- Commit `index.html`, `styles.css`, `assets/`, `.gitignore`, `.nojekyll`, `README.md`, and any requested docs.
- Keep local visual QA screenshots ignored unless the user explicitly asks to upload them.
- If `gh` is unavailable but SSH works, use an SSH remote such as:

```bash
git remote set-url origin git@github.com:OWNER/REPO.git
git push -u origin main
```

