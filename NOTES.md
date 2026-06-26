# Project Notes — Ariel's Money Garden

## What this is
A single-page fun investing site for Ariel: watermelon/purple/green themed, three example
"safe" investment portfolios, each with its own compounding-interest calculator and a
goofy animation + sound effect that plays when you hit calculate.

Live at: https://distant0bserver.github.io/ariel-money-garden/

Site files live in `docs/` (GitHub Pages is configured to deploy from `main` branch, `/docs` folder).

## What we built today (2026-06-26)
- Built `docs/index.html` as a single self-contained file (HTML + CSS + JS inline, no build step).
- Three portfolio sections, each with a compounding interest calculator:
  - 🐒 "Don't Touch It" — low-risk savings/bonds, monkey-throwing-cash animation
  - 🛞 "Cruisin' Comfortably" — index fund mix, spinning rims animation
  - 🚬🍾 "Grown Folks Business" — growth-tilted long-horizon mix, cigar smoke / bottle / bill rain combo animation
- Compounding math: standard monthly-compounding formula with monthly contributions
  (`balance = P(1+r)^n + PMT * ((1+r)^n - 1)/r`).
- Animations: emoji elements spawn at the **bottom** of the portfolio card, bounce up
  past the **top**, then fall back down and out the bottom (unified `flyArc` CSS keyframe,
  driven by `--dx`, `--bounce`, `--fall`, `--rot` custom properties set in JS per emoji).
- Two sound effects wired to play on calculate (user-supplied local mp3s, copied into
  `docs/sounds/`): `got-your-money.mp3` plays immediately, `damn.mp3` plays ~0.7s later.
- Disclaimer text intentionally does NOT mention AI or describe the page as made by an
  "AI" or "watermelon-loving friend" — kept neutral/professional-sounding per request.
- Default calculator values: $100,000 starting amount, $1,000/month contribution,
  across all three portfolios.
- Repo: github.com/distant0bserver/ariel-money-garden, pushed to `main`, GitHub Pages
  enabled (Deploy from branch → main → /docs).

## How to keep updating it
- Edit `docs/index.html` directly (everything — markup, styles, script — is in that one file).
- To change calculator defaults: search for `id="p1-principal"` etc. (p1/p2/p3 per portfolio).
- To change animation behavior: look at `spawnFlying()` and the `flyArc` keyframe in the
  `<style>` block — duration/spread/rotation per animation type are set in `playAnimation()`.
- To swap sound effects: replace the mp3 files in `docs/sounds/` (keep the same filenames,
  or update the `<audio>` tag `src` attributes near the bottom of the file).
- After editing, commit and push to `main` — GitHub Pages auto-redeploys from `/docs`.
