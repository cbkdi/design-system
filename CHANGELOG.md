# CHANGELOG

## 2026-04-24 — § glyph retired; numbered-eyebrow pattern codified (U11)

Reconciles `DESIGN.md` with the as-built cbkdi.com after the glyph audit at [cbkdi/cbkdi-website#12](https://github.com/cbkdi/cbkdi-website/pull/12).

- **Removed:** the `§-anchor` rule for `/writing` h2s. The companion CSS rule never shipped a real consumer in the reference implementation, and the glyph was not earning signal against the already-numbered eyebrow system.
- **Removed:** `§` prefix from rendered eyebrows (`§ 01` → `01`), engagement card tags (`§ A · Retainer` → `A · Retainer`), contact-form eyebrow, 404 stamp, and `/writing` foot stamp (`CBKDI · § Writing` → `CBKDI · Writing`).
- **Added:** `SectionEyebrow` component spec replacing the retired `SectionAnchor`. Documents the `NN · Label · <rule> · Secondary` pattern the marketing sections have been running for a revision.
- **Added:** Chrome Don't — "don't reintroduce the `§` glyph in rendered copy" — so the retirement holds across future drafts.
- **Trimmed:** stale reference to "In the Room" chip tags in the shape / pill-radius section (never implemented).

Tokens unchanged. Type scale unchanged. No color or radius changes.

## 2026-04-24 — Face selection committed (U6/U7/U10)

- **Display:** Instrument Serif (Google Fonts, OFL) — replaces Georgia placeholder
- **Reading body (/writing):** Source Serif 4 (Google Fonts, OFL) — replaces Inter fallback
- **Mono:** IBM Plex Mono (Google Fonts, OFL) — replaces JetBrains Mono placeholder
- **Body (UI):** Inter — retained
- **Wordmark:** moved from Inter Semibold to IBM Plex Mono Medium; tracking 0.08em → 0.14em
- **Line-heights / tracking** re-tuned for new face metrics

- **/writing vocabulary** fleshed out under Layout: reading face, reading scale, 64ch measure, TOC sticky sidebar with `font-weight: 500` active state, breadcrumb middle-ellipsis truncation at 40ch, revision-stamp placement, footnote typography.

- **Do's and Don'ts** additions: wordmark-face Don't.

- Zero paid faces committed. All four faces are free (Google Fonts, OFL).

- Rubric: passes R13a on all three comps (Hero, About, /writing) in both light and dark modes. See `rubric-walkthrough.md` in the comps package.
