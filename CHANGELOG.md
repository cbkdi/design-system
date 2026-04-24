# CHANGELOG

## 2026-04-24 — Face selection committed (U6/U7/U10)

- **Display:** Instrument Serif (Google Fonts, OFL) — replaces Georgia placeholder
- **Reading body (/writing):** Source Serif 4 (Google Fonts, OFL) — replaces Inter fallback
- **Mono:** IBM Plex Mono (Google Fonts, OFL) — replaces JetBrains Mono placeholder
- **Body (UI):** Inter — retained
- **Wordmark:** moved from Inter Semibold to IBM Plex Mono Medium; tracking 0.08em → 0.14em
- **Line-heights / tracking** re-tuned for new face metrics

- **/writing vocabulary** fleshed out under Layout: reading face, reading scale, 64ch measure, TOC sticky sidebar with `font-weight: 500` active state, breadcrumb middle-ellipsis truncation at 40ch, revision-stamp placement, footnote typography, §-anchor use rule.

- **Do's and Don'ts** additions: wordmark-face Don't; §-anchor Do under Chrome.

- Zero paid faces committed. All four faces are free (Google Fonts, OFL).

- Rubric: passes R13a on all three comps (Hero, About, /writing) in both light and dark modes. See `rubric-walkthrough.md` in the comps package.
