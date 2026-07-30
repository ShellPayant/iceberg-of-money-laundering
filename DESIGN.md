# DESIGN.md · The Iceberg of Money Laundering

House rules for anyone (human or Claude) writing, illustrating, or coding for this project. Derived from what is actually on the page, not from aspiration. When in doubt, open `essay.html`, find the nearest existing example, and match it. This file supersedes `visual-plan.md` / `visual-plan-v2.md` (kept as history).

One meta-rule governs everything below: **this work must read and look hand-made.** The author is a real investigator with a day job in fraud security; the essay's credibility depends on nothing about it smelling machine-generated. Section 7 lists the specific tells to avoid.

And one counterweight: **these are guardrails, not a cage.** Invention is expected here. The best figures in this project came from ideas nobody asked for (a scanner turned on the police, a withheld frame in a contact sheet, a wall that is also a bar chart). Propose the strange version first: a new figure form, a new interaction, a beat played against expectation. The rules below define what the idea must wear (the palette, the voice, the integrity labels, the restraint), never how far it may go. If a concept is exciting but breaks a rule, say so and pitch it anyway; rules bend by decision, not by drift.

---

## 1 · Voice

First person singular for the author ("I read the experts' books, dug up FBI case files"). First person plural for enforcement ("us: just as clever, working entirely to catch them"). Second person for the reader, who plays the launderer for the length of the essay ("For the length of this essay, the money is yours"). The coda acknowledgment is finalized; never touch it.

What the voice does:

- **Kicker sentences.** Short, blunt, paragraph-ending. "That's the tell." "You never even see it happen." "Let's go down." Use them to land a point, not as decoration.
- **Deliberate fragments.** "Harder than the movies make it look." A fragment is a beat, used maybe once per section. Never stack them.
- **Coined rules, bolded once, repeated later.** "**every control measure creates a customer-experience bypass, and the bypass is the way in.** Remember that." New jargon gets bold on first use (**bank drop**, **opsec**, **smurfing**), plain text after.
- **Personal evidence over generic authority.** The author was a broke student in Paris; works security at a logistics giant; chased €200,000 through three banks. New prose should hang claims on lived specifics like these, or on named sources, never on "experts say".
- **Concrete numbers and named things.** €1.80, 30,000 balls of dough, Subito.it, Revolut, twelve accounts. If a sentence can carry a real number or a real name, it should.
- **Rhetorical question, then a blunt answer.** "Does it hold up? Consider the case..." Sparingly.
- **Dry irony, never jokes.** "The taxman congratulates you on your investment instincts." No winking at the reader, no exclamation marks, anywhere.
- **Ethics stitched inline.** Techniques are described only when patched or historic, and the essay says so ("if I can walk you through it at all, it's because it no longer works"). Protective advice appears in-flow (the ID-watermark aside). The foot-note disclaimer frames the whole essay; new content must stay consistent with it.
- **Vulgarization as creed.** Every concept must survive being explained to a non-expert without losing precision. If a sentence needs the reader to already know finance, rewrite it.

Spelling and tics: the author's usage is mixed ("favorite" but "colours" in captions). Match the nearest neighbouring text; do not normalize either way. Smoothing the author's small inconsistencies is how text starts smelling artificial.

## 2 · Punctuation and mechanics (hard rules)

- **No em dashes in shipped files** (`essay.html`, `index.html`). The draft (`essay.md`) may use them; converting them to colons, periods, parentheses, or "·" is part of the build pass. Check: `grep -c "—" essay.html` must be 0. (As of 2026-07-28 there are 24 stragglers pending a sweep; do not add more.)
- **Curly quotes inside JS strings.** `CONTENT`/`TERMS`/`NOTES` strings are double-quoted; any quote or apostrophe inside the text must be ’ “ ” ‘, never straight.
- Footnote markers `{n}` in prose, sequential 1→28 in reading order (`node order.mjs`). Tooltip terms as `{{term}}`.
- Captions: two or three beats, ending on a turn. "Twenty-one million euros, counted by hand. Most of it bricked up inside the walls of chief inspector Óscar Sánchez Gil, head of Madrid's financial-crime unit: the cash the best network in Europe could not get rid of."
- Plate labels: mono, uppercase via CSS, two or three words ("THE RECORD", "SPECIAL COUNTERS").
- Content edits land in three places: `essay.html`, `essay.md`, and the `#methods` JSON island.

## 3 · Palette and typography

Tokens (never invent new colors; tint with alpha instead):

| token | value | role |
|---|---|---|
| navy | `#0B1626` | page, depth |
| abyss | `#04070E` | deepest zones |
| bone | `#EDE8DF` | body text, paper, light zones |
| ice | `#7FB3D5` | lines, labels, glow |
| danger | `#C96F5F` | the crime, and only the crime |
| green | `#3E7C4F` | clean-money accents only |

Type: serif (Iowan Old Style stack) for prose and display numbers; system sans for captions and UI; mono (SF Mono stack) for labels, chips, evidence apparatus. Mono labels always uppercase with wide letter-spacing (.14em to .22em). No webfonts, no Inter, no gradient text, ever.

**The dashboard is not a second brand.** The data companion (and any future dashboard, template, or derived system) runs on the same six tokens: ice with alpha steps for series and chips, bone for numbers, danger for crime only, green for clean-money semantics. It never grows its own accent set. Stock framework hues (Tailwind's teal `#5EEAD4`, sky `#7DD3FC`, amber `#FBBF24`, coral `#F87171` and their neighbours) are a named AI tell; if one appears anywhere, it is a bug. Semantic state colors are not accents and must still be derived from the six.

**Danger-red discipline:** red marks "this is the crime" and nothing else (one red brick in a wall of ice ones, the office million in the count, the SECRETO stamp). If red appears twice in one figure, one of them is wrong. The same law generalizes beyond color: spend the boldness of any figure in exactly one place (one reveal, one interaction, one loud element) and keep everything around it quiet.

## 4 · Illustration (vector)

All illustration is bespoke hand-built inline SVG. **Never AI-generated imagery, never stock, no exceptions.** The four full-bleed plates, nineteen spots, and the panorama are done; new figures must sit beside them as siblings.

- One subject per figure, generous negative space, thin ice strokes (1 to 1.5px) on dark ground, sparse fills at low alpha.
- Scenes are ordinary on the surface and wrong underneath (a living room; the wall is full of cash). That contrast is the house move.
- Diagram grammar: mono callouts with elbow leader lines and a dot anchor, corner registration ticks on evidence frames, chips (dark pill, mono text) bottom-left for the plate name and bottom-right for source or credit.
- Motion is quiet and slow (6 to 10s glow pulses, drifting motes) or scroll-driven; every animation gated behind `@media (prefers-reduced-motion: reduce)`. Nothing bounces, nothing spins, nothing eases dramatically.
- Numbers can be figures: unit grids where one tick = one real thing (a €10,000 brick), counts that are checkable against the reporting. Round only with "≈".

## 5 · Photography (evidence doctrine)

Vectors explain; photographs testify. Real photos appear only where a real photo beats any illustration (the €21m seizure; Obiang's mansion and supercars are the next candidates).

- **Sources:** police/agency handout material or licensable press photos only. Never AI images, never stock, never watermarked press exclusives, never Getty/AP/AFP agency shots we cannot license. Document provenance and rejected candidates in `img/SOURCES.md`.
- **Treatment:** the asset stays untouched colour on disk; the grade is live CSS. Two stacked imgs: colour original under, duotoned copy on top (`#duo-ice` inline SVG filter, sRGB, navy→slate→dimmed-ice→pale-ice), `contrast(1.12) brightness(.93)` pre-grade, edge vignette. Hover fades the duotone to reveal true colour (hover-capable devices only). `filter:url()` cannot be transitioned; fade opacity instead.
- **Chrome:** corner ticks, plate chip, credit chip ("EVIDENCE PHOTO · POLICÍA NACIONAL"). Alt text describes the photograph plainly.
- **Integrity:** any composite of drawing and photograph, or any reconstructed document, is labelled as such in-frame or in the caption. Reconstructions carry "not the original document". Do not imply we hold imagery we do not hold.
- **Gotcha:** slot `<img>`s must not use `loading="lazy"` (they sit at `display:none` until loaded and Chrome never fetches them).

## 6 · Interaction grammar

- Scroll is the primary engine (pins, scrubbed steps, the depth gauge). Standalone timers only in scratch demos; production animations key off scroll or viewport entry.
- Interactions are opt-in and discoverable, never demanded: hover reveals, a drag handle, a replay chip. No instruction overlays, no "scroll down!" prompts beyond the single hero cue.
- Every stateful figure has a reduced-motion path that lands on the finished state.
- External links from figures open in a new tab (`noopener`) and go to primary reporting (the Guardian piece for the Sánchez case), with keyboard access (role="link", Enter/Space).

## 7 · The anti-AI checklist

The article must never look or read machine-made. These are the tells; treat every one as a bug.

**Visual tells (banned):**
- Purple/indigo-to-teal gradients, glassmorphism panels, glowing gradient borders: the default AI-SaaS look.
- Emoji anywhere in headings, labels, or UI. Sparkle/✨ iconography. Rocket ships.
- Hyperreal 3D renders, cinematic volumetric fog, lens flares, bokeh, over-saturated "epic" lighting.
- Corporate-Memphis blob people, isometric illustration-pack art, icon-grid feature sections.
- Uniform rounded-XL cards with drop-shadow soup; centered symmetric compositions everywhere.
- Garbled pseudo-text baked into artwork (our art carries no baked text at all; words are HTML).
- Default-stack sameness: Inter or Space Grotesk as the "safe" face, gradient blobs, 12-column card grid.
- The named AI clusters (from Anthropic's own design guidance): warm cream `#F4F1EA` + serif display + terracotta accent; near-black with a lone acid-green pop; broadsheet hairlines with dense columns; accent bars on rounded cards. Our bone-paper exhibits brush the first cluster; they stay legal only because the paper is diegetic (a real document form) and the red is crime-only. Keep it that way.
- Numbered markers (01 / 02 / 03) and other structural devices where order or hierarchy carries no real information. Structure is information: a device must encode something true about the content or it goes.

**Writing tells (banned):**
- Em dashes in shipped copy (house rule doubles as an AI-tell rule).
- The vocabulary: delve, dive into, landscape, tapestry, crucial, pivotal, robust, seamless, leverage, journey, roadmap, "in today's world", "at the end of the day".
- The constructions: "It's not just X, it's Y". "X isn't about Y; it's about Z". Rule-of-three triads in every sentence. Colon headlines ("Laundering: Why It Matters"). "In conclusion", "Moreover", "Furthermore", "It's important to note".
- The rhythm: every paragraph the same length, every sentence medium-sized, perfect parallelism. Human paragraphs breathe; some are one line.
- Structure crutches: bullet lists in place of argument (bullets are for reference material like this file, never for the essay), bold scattered for emphasis rather than reserved for coined terms, a tidy moral summary at the end of each section.
- Hedging and throat-clearing: "arguably", "generally speaking", "various", "numerous". Say the number or cut the sentence.

**Positive test:** a new passage passes when it contains at least one of: a first-person specific, a named real thing, a checkable number, or a coined rule doing work. If it contains none, it reads like filler; rewrite it.

## 8 · Pre-ship checklist

1. `grep -c "—" essay.html` → 0 (and no straight quotes inside JS content strings).
2. `node check.mjs` → ERRORS 0; `node order.mjs` → footnotes 1→28 in order (regenerate the .mjs QA scripts if missing).
3. Reduced-motion pass: every new animation inert, every stateful figure landing on its finished state.
4. Screenshot every new graphic as PNG stills and eyeball for label overlap (GIFs crush faint gradients).
5. Content parity: `essay.html` = `essay.md` prose = `#methods` island.
6. Sync: copy `essay.html` → `iceberg-site/essay.html`, regenerate `index.html` (meta block splices after the viewport tag), and mirror `img/` in both locations.
7. Credits and provenance: every photo has an in-frame credit and an entry in `img/SOURCES.md`.
8. Read the new text aloud once against Section 7. If any sentence could have been written by nobody in particular, it is not done.
