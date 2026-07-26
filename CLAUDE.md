# CLAUDE.md — The Iceberg of Money Laundering

Handoff context for any Claude Code session working on this project. No secrets here; fine to keep in the repo.

## What this is
An interactive, self-contained HTML essay — a scroll-driven "descent" through the techniques of money laundering, tier by tier. Editorial / investigative-long-read style (think NYT/Guardian interactive).

Files:
- `essay.html` — the working source. Everything (CSS, JS, SVG) is inlined; the only dependency is an inlined Motion One bundle. This is what you edit.
- `essay.md` — prose mirror of the same text (plain Markdown, footnotes `[^1]`–`[^19]`). Lives in the parent project folder; keep it in sync on prose edits.
- `index.html` — the PUBLISHED copy = `essay.html` + a `<head>` block of preview meta (OpenGraph/Twitter/favicon). After a content edit, regenerate it: copy `essay.html` → `index.html` and re-add the meta block (or ask Claude to).
- `share.png` — 1200×630 social preview card (rendered from the hero).

Rule: content edits land in BOTH `essay.html` and `essay.md`, AND in the hidden `#methods` JSON island inside `essay.html` (it retells each technique — keep it consistent). Figures/interactives are HTML-only.

## essay.html internals
- `NOTES[]` — footnotes; inline markers `{n}` in the prose.
- `TERMS{}` — `{{term}}` hover tooltips.
- `FIGS{}` — inline SVG/HTML figures (lifestyle gap, live org chart, leaked-manual exhibit, Obiang seizure, …).
- `PINS{}` — scroll-pinned multi-step diagrams. Step machinery: `.pd-frame[data-step="N"]`; `.s0/.s1…` reveal from step N onward; `.x0/.x1…` hide after; `.greyable`; `.route` draws via stroke-dashoffset.
- `bleedArt(kind)` — full-bleed animated backgrounds: `hero`, `coda`, `glass`, `deep`.
- `phArt` / `phGlyph` — the ~19 inline spot-illustrations (`IMGS` map).
- `panoBlock` / `shopGlyph` — the draggable storefront panorama.
- `#methods` — hidden JSON "field guide" island.

## GOTCHA (silently breaks the page)
Strings in `CONTENT` / `TERMS` / `NOTES` are DOUBLE-quoted, so any apostrophe or quote INSIDE the text must be a CURLY character — ’ “ ” ‘ — never a straight `'` or `"`. A straight quote ends the JS string and breaks rendering.

## Art direction
All art is bespoke animated vector (hand-built SVG + subtle CSS animation), NOT AI images — cohering with the vector figures is the whole point. Every animation is gated behind `@media (prefers-reduced-motion: reduce)`. Recurring motif: the illicit element in a scene ignites in danger-red (`var(--danger)`, `#C96F5F`) — the "this is the crime" beat (borrowed from the source documentary). Palette: navy `#0B1626`, ice `#7FB3D5`, bone `#EDE8DF`, danger `#C96F5F`.

## Validate before shipping (headless Playwright + Chromium)
- `node check.mjs` → must print `ERRORS 0`.
- `node order.mjs` → footnote citations must read 1→28 in order.
- `node shotplates.mjs` / `shotspots.mjs` / `shotpano.mjs` → render PNG stills; eyeball EVERY graphic for text overlap and loop until clean. (GIFs crush faint gradients — use PNG stills.)
- New machine setup: `npm i playwright` then `npx playwright install chromium`. (These `.mjs` scripts are optional QA tooling — regenerate if missing.)

## Current state
Writing, 28 footnotes, tooltips, `#methods` layer: done. Signature interactives (annotated manual, live org chart, scroll-scrubbed descent map) and the motion layer: done. All 4 full-bleed plates, all 19 inline spots, and the storefront panorama: done as animated vector. Publishing prepared in this folder (index.html + share.png + README).

## Remaining
1. Publish to GitHub Pages — repo `iceberg-of-money-laundering`, enable Pages on `main` / root. Replace `YOURUSER` in `index.html` and `README.md` with the real GitHub username so the preview card resolves.
2. Mobile/responsive QA at 360–390px (SVG figure labels get tight; check pinned sections and the pano drag).
3. Optional: French translation (keep "justificatif"; interactives carry over since they're code, not images).

## Voice
First-person "I" for the author; "we/us" for enforcement/investigators. The coda acknowledgment is finalized — leave it as written.
