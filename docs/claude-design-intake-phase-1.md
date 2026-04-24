# Claude Design intake — Phase 1 (design system finalization)

Copy the two fields below into `claude.ai/design` when starting the Phase 1 session. Phase 1 finalizes the design system (faces, wordmark, `/writing` vocabulary); Phase 2 (the cbkdi.com refresh) is a separate session once Phase 1 commits land.

Form fields: `Company name and blurb`, GitHub repo URL (`https://github.com/cbkdi/design-system`), and `Any other notes?`. Skip the `.fig` upload and the `fonts/logos/assets` upload — there are none, the repo is the whole context.

---

## Field 1 — Company name and blurb

```
CBKDI (CBK Development Intelligence) — a one-person consulting practice working on systems, process, and product design for operators, viewed through a sponsor-side real-estate-development lens. Visual language: editorial voice inside opinionated structural chrome — warm dark near-black, single purple accent, three-face typography, first-person copy, restrained flourish.
```

---

## Field 2 — Any other notes?

```
This design system is at v0.1 — infrastructure is done, visual decisions are still open. Treat this as a finalization pass, not a greenfield build.

Read the repo first. The open items live in:

- docs/plans/2026-04-23-001-feat-cbkdi-design-system-plan.md — units U6 (face selection), U7 (wordmark refinement), U10 (/writing vocabulary).
- DESIGN.md — the R13a rubric in Do's and Don'ts is your acceptance test; the enumerated "02ui moves borrowed" in Shapes is the positive reference (translated away from 02ui's pixel-art costume into an editorial register).
- tokens.css — face-family stacks are currently placeholders (Georgia / Inter / JetBrains Mono). Iterate and commit.

Commit these four decisions:

1. Display serif. Free candidates: Fraunces, Instrument Serif, Source Serif 4. Paid candidates from the brainstorm: GT Sectra, Migra, Beatrice Display, Editor's Note, Romie, Tiempos Headline, Equity Caps, GT Super. Default to free; if a paid face is meaningfully stronger against the rubric, surface it with license cost for explicit approval before committing.

2. Monospace. Mono is load-bearing for the "systems" signal in this brand — it labels, stamps, and measures. Pick for that, not for code display. Free: JetBrains Mono, Geist Mono, IBM Plex Mono. Paid: Berkeley Mono (~$75 per seat, site-license tiers higher). Same approval rule as above if going paid.

3. Reading body for /writing long-form. Options: stay with Inter, switch to Source Serif 4, switch to Tiempos Text. Decide after a real long-form comp, not a one-line mock.

4. Wordmark. Today: leading purple dot + "CBKDI" in tracked uppercase. Evaluate against the chosen display face — keep, move to mid-height inline, retire entirely, or replace with a structural mark (em-rule, middle-dot). Commit with specific markup and sizing.

Process:

Work in real CBKDI copy, not lorem ipsum — the prior Newsreader attempt failed because it was evaluated on placeholder text and read as generic premium consulting (Stripe-Press-adjacent, which is not what this is). Render three comps with candidate combinations:

- Hero — "Senior judgment. Durable systems." headline + existing subhead
- About block — Conor's bio paragraphs
- /writing post mockup — any representative passage

Apply the R13a rubric to each comp — must-haves (all four required), should-haves (3 of 5), no must-not-haves. Document why each finalist passes or fails. References worth studying directly are 02ui.com (for the chrome + type-contrast register) and Ink & Switch long-form essays (for reading measure and rhythm) — both live outside this repo.

Constraints:

- Voice: first-person ("I", not "CBKDI" in third person), hyphens not em dashes, no "Fractional Development Lead" as the primary headline, no third-person "CBKDI does X" in body copy. These are site-wide rules in DESIGN.md Do's and Don'ts.
- Identity: typographic only. No pictorial logos, no stock photography, no figurative illustration.
- Palette: single-accent purple, editorial-flat. No shadows, no blur surfaces, no second accent hue.
- Budget: any paid face needs explicit approval before committing. Default to free.

Deliver:

- Proposed edits to tokens.css (face-family stacks, line-height and tracking reviewed against the chosen faces and adjusted if needed).
- Proposed edits to DESIGN.md — Typography section reflects the committed faces with rationale, Components.wordmark documents the committed treatment with exact markup, and the /writing vocabulary is fleshed out under Layout (reading face, reading type scale, column measure in ch, line-height, TOC sidebar pattern at ≥1080px with font-weight:500 active state, breadcrumb truncation rule, revision-stamp placement, footnote typography).
- One real-copy comp per surface (Hero / About / /writing) in both light and dark modes.
- R13a rubric walkthrough per comp — which must-haves / should-haves / must-not-haves hit, and why the finalist won.
- Short summary of what changed and what is deliberately deferred to the follow-on website refresh.

Do not redesign cbkdi.com in this pass. The website refresh is a separate session once these system decisions land.
```

---

## Phase 2 — later

Once Phase 1 commits land (tokens.css + DESIGN.md updated with real faces, wordmark, /writing vocab), start a separate Claude Design session for the cbkdi.com refresh. That prompt will reference the now-finalized `DESIGN.md` as the whole spec and ask for the section-by-section re-skin + copy pass per plan units U7 (wordmark implementation in `cbkdi-website/src/components/layout/Header.astro`), U8 (RevisionStamp + interaction states), U9 (copy pass + `src/data/` extraction), U11 (lint + ship).
