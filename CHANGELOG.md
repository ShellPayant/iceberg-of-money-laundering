# Changelog

Notable changes to the published essay. The working canon lives in DESIGN.md; content edits land in essay.html, essay.md (source draft, kept off-repo) and the #methods island together.

## 2026-07-29

### Added
- Plate B (The record) carries its first real evidence photograph: a Policía Nacional handout still from the November 2024 search, an investigator's hand pressing vacuum-sealed rolls of euros. The asset stays untouched colour on disk; a live navy/ice duotone (inline SVG filter `#duo-ice`, sRGB) grades it into the palette, and hovering reveals the true colours. Corner ticks, plate chip and credit chip frame it as an exhibit.
- `img/` assets with provenance and rejected-candidate notes (`img/SOURCES.md`), including the portrait alternates from the same police set.
- `DESIGN.md`: the house style canon. Voice and sentence craft, punctuation rules, the six-token palette discipline, illustration and evidence-photo doctrine, interaction grammar, the anti-AI-tells checklist, and the pre-ship checklist. Supersedes the visual-plan documents.
- `.nojekyll` so GitHub Pages serves every asset verbatim.

### Changed
- The Record caption now names chief inspector Óscar Sánchez Gil, head of Madrid's financial-crime unit.
- `CLAUDE.md` points to `DESIGN.md` and records the evidence-photograph doctrine and slot mechanics.

### Fixed
- Image slots could never swap in a real file: a `loading="lazy"` image held at `display:none` is never fetched by Chrome. Lazy loading removed from slot images; the drop-in machinery now works.

## 2026-07-26

- Initial publication: the full essay with 28 footnotes, the field guide, the signature interactives, four full-bleed plates, nineteen spot illustrations and the storefront panorama, all as bespoke animated vector. Em-dash appositives rewritten in prose and README.
