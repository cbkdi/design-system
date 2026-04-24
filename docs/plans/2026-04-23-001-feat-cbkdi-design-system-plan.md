---
title: CBKDI Design System and Website Refresh
type: feat
status: active
date: 2026-04-23
deepened: 2026-04-23
origin: 05 - Marketing/design-system/docs/brainstorms/2026-04-23-cbkdi-design-system-requirements.md
---

# CBKDI Design System and Website Refresh

**Target repos:**
- `cbkdi/design-system` (new public repo, Tailwind v4 CSS-first token authoring + DESIGN.md) — to be created under the `cbkdi` GitHub org.
- `cbkdi/cbkdi-website` (existing) at `05 - Marketing/Website/cbkdi-website/` — consumes tokens from `cbkdi/design-system`.

Paths in this plan are repo-relative. Website-repo paths are rooted at `05 - Marketing/Website/cbkdi-website/`; design-system-repo paths are rooted at `05 - Marketing/design-system/` during initial development and move to the cloned `cbkdi/design-system` checkout once the repo is created.

---

## Overview

Build `cbkdi/design-system` as CBKDI's first-class brand artifact — a public, lint-checked Tailwind v4 `@theme` token set plus a canonical `DESIGN.md` that Claude Design can consume — and use it to refresh `cbkdi.com`. The refresh applies editorial voice inside opinionated structural chrome (02ui.com-informed), lands a new `/writing` surface scaffold (tokens specified; live route ships with the first real post, not before), and brings the site copy forward to the 2026-04-23 positioning refinement (systems / process / product design through a sponsor-side real-estate-development lens; fractional dev-lead secondary, not the headline).

This is a cross-cutting, strategic change. Two repos, one ship unit (copy + visuals refresh together).

---

## Problem Frame

See origin: `05 - Marketing/design-system/docs/brainstorms/2026-04-23-cbkdi-design-system-requirements.md`.

Short form: the current cbkdi.com was built to sell one service lane (deal underwriting / "Fractional Development Lead"); the practice now leads with systems / process / product-design consulting viewed through a sponsor-side RE-development lens. Visual identity has not caught up to either the 2026-03-23 messaging pivot or this further refinement. Separately, Claude Design has launched and consumes a DESIGN.md artifact — CBKDI needs a real, machine-readable brand system that refreshes cbkdi.com, governs future surfaces as they refresh, and feeds Claude Design.

---

## Requirements Trace

Origin requirements carried forward. All of R1–R14, R5a, R8a, R13a from the brainstorm are addressed by implementation units below. AE-level acceptance examples are enumerated in test scenarios on the units that own them.

- R1. Public repo based on `google-labs-code/design.md` under `cbkdi/design-system` — U1. (Fork-vs-template decision is in Key Technical Decisions; revisit per doc-review findings.)
- R2. Passes `@google/design.md lint` (including WCAG AA contrast in both modes, via CSS-first dark-mode selectors) — U11.
- R3. `DESIGN.md` is self-contained and portable — U3.
- R4. Top-level `README.md` explains what, how, and adoption — U1.
- R5. Editorial voice inside opinionated structural chrome — U3, U8.
- R5a. Reference anchor captured as an enumerated "02ui moves borrowed" list — U3.
- R6. Dark warm near-black field; single purple accent; no secondary brand colors — U2.
- R7. Three-face type system (display serif, Inter body + reading serif for long-form, monospace chrome) — U2, U6.
- R8. Structural chrome does work: breadcrumbs / TOC / revision stamps / soft-cornered dark-card containers / §-anchors used sparingly — U8.
- R8a. Interaction states specified for every chrome element; non-color active-TOC differentiator; reduced-motion respected — U8.
- R9. Typographic wordmark refinement, no pictorial mark — U7.
- R10. Re-skin ships as one unit with the 2026-03-23 copy follow-on pass; no phased ship with stale copy — U5, U9, U11.
- R11. `/writing` vocabulary specified in v1; live route ships with first post, not empty — U3 (spec), U10 (scaffold — scope revisit pending).
- R12. Tokens imported from design-system; no duplication — U4.
- R13. Claude Design intake blurb maintained in repo — U3 (authored), U9 (aligned post-positioning).
- R13a. "Visibly, unmistakably CBKDI" rubric — U3 (authored), U11 (applied).
- R14. CSS-first token flow; vendored at build time; no runtime external fetch — U2 (authored), U4 (vendored).

**Origin actors:** A1 (Conor Keilty, principal / decision authority), A2 (Claude Design, programmatic consumer), A3 (future contributors / contractors), A4 (prospective clients — Steve / Erich / Kreider exemplars).

**Origin flows:** F1 (hand CBKDI to Claude Design), F2 (refresh cbkdi.com using the design system), F3 (future surface adopts the system, opportunistic).

---

## Scope Boundaries

- **Not a pictorial logo** — identity stays typographic.
- **Not a rebrand** — CBKDI / CBK Development Intelligence, purple accent, Inter body, restrained editorial voice are preserved.
- **Not a cbkdi.com restructure** — single-page anchor flow stays; only the `/writing` scaffold is added.
- **Not case-study publishing** — separate effort. The design system accommodates; v1 does not require any.
- **Not covering all CBKDI surfaces in v1** — Hilltop (`hilltop.cbkdi.com`), Node proposal generator, email signatures, Kreider handouts adopt opportunistically as revised.
- **Not writing essays** — content production is not in this plan. Live `/writing` route ships with the first real post, which is a separate future effort.
- **Not a demand-gen initiative** — design-system work is a brand-quality lever, not a distribution lever.
- **No automated upstream fork sync** — pulling from `google-labs-code/design.md` is a manual, occasional practice.

### Deferred to Follow-Up Work

- **First `/writing` post + live route flip.** A future effort outside this plan. This plan specifies the layout + tokens; the go-live happens when the first post is ready.
- **Tailwind-export compatibility with upstream `@google/design.md` CLI.** CBKDI is CSS-first (R14), so the upstream CLI's v3-JSON export is not used. If a future surface needs the v3 export, that's its own effort.
- **Non-website surface adoption** — Hilltop re-skin, proposal template PDF regeneration, email-signature update, Kreider handout restyle. Each surface revises opportunistically on its own cadence.
- **A11y audit beyond WCAG AA contrast** — only contrast is asserted by R2. Full audit deferred.

---

## Context & Research

### Relevant Code and Patterns

- `05 - Marketing/Website/cbkdi-website/src/styles/global.css` — current `@theme` block: brand-purple scale anchored on `#4f3d78` at 700, 4 surface tokens (`--color-surface-light #fafafa`, `--color-surface-dark #111111`, two card variants). No type-scale or neutral-gray tokens yet; grays are literal `[#4a4a4a]`/`[#aaa]`/`[#ddd]`/`[#2a2a2a]` arbitrary-value utilities across every section component.
- `05 - Marketing/Website/cbkdi-website/src/layouts/BaseLayout.astro` — inline `<head>` script reads `localStorage.theme` then falls back to `prefers-color-scheme`; applies `.dark` class before paint. Do not break this.
- `05 - Marketing/Website/cbkdi-website/src/layouts/PageLayout.astro` — Header + `<main>` + Footer composition. New `/writing` page uses this.
- `05 - Marketing/Website/cbkdi-website/src/components/layout/Header.astro` — wordmark at lines 15–18: a purple-dot `<span>` + tracked-uppercase `CBKDI` text. Nav items hard-coded inline; needs edit to add `/writing` when that route goes live.
- `05 - Marketing/Website/cbkdi-website/src/components/layout/ThemeToggle.svelte` — Svelte 5 rune-based toggle, hand-rolled (no `mode-watcher` dep). Subscribes to `matchMedia` changes only when no explicit user choice is stored. Do not re-add `mode-watcher`.
- `05 - Marketing/Website/cbkdi-website/src/components/sections/*.astro` — six section components (Hero, About, Services, Engagement, Contact, Testimonials) + the consistent pattern `<section id="..." aria-labelledby="..." class="max-w-[66rem] mx-auto px-4 sm:px-6 lg:px-8 py-16 md:py-20">`. Copy is inline or in local `const` arrays — not extracted to `src/data/` yet.
- `05 - Marketing/Website/cbkdi-website/src/middleware.ts` — per-request nonce CSP middleware. **CSP `style-src` does not permit external style origins** — token flow must vendor CSS at build time, not fetch at runtime.
- `05 - Marketing/Website/cbkdi-website/docs/design-audit.md` — authoritative current token set: full light/dark palette tables, Inter-only typography with 6-token `clamp()` scale (`f-sm` through `f-xl`), 8-token spacing scale, max-width `66rem`, wordmark spec (0.4em dot, 0.08em tracking, weight 600), full content inventory. This file is the starting point for the authored `@theme` in `cbkdi/design-system`.
- `05 - Marketing/Website/cbkdi-website/CLAUDE.md` — project constraints: `output: 'server'` is required (middleware must run); do **not** enable `experimental.csp`; do **not** create `public/_headers`; section components need `id` for anchor nav; Phase 2 copy-extraction to `src/data/` is a live prereq.
- `05 - Marketing/Website/cbkdi-website/src/lib/utils.ts` — `cn()` helper stub; `clsx` + `tailwind-merge` already in deps. Ready to fill in when needed.
- `.claude/memory/project_cbkdi_positioning.md` — 2026-04-23 positioning: systems / process / product design (through RE-dev lens) is the headline; fractional dev-lead secondary.
- `.claude/memory/project_website_status.md` — prior Newsreader-serif refresh was rejected; document the anti-regression guidance inline.
- `.claude/memory/reference_github_accounts.md` — cbkdi GitHub account scoping; use scoped-remote URL pattern `https://cbkdi@github.com/cbkdi/design-system.git` for the new repo.

### Institutional Learnings

- **Dropbox + Windows EPERM on `node_modules/`, `.astro/`, `.wrangler/`, `dist/`.** Set the `com.dropbox.ignored` ADS before first `npm install`; `.gitignore` alone doesn't stop Dropbox sync. (From hilltop-investor-page solutions.) Applies to the new design-system repo's dev dir.
- **Wrangler version pairing with the Astro adapter** — pin, don't blindly bump on CLI nag. (Applies to cbkdi-website when wrangler nags during the refresh ship.)
- **Design-handoff side-by-side render gate** — lock a side-by-side comparison (design-system reference + built cbkdi.com) at the start of the visual-refresh phase to catch drift from pre-existing components that weren't in the refresh scope.
- **Preserve existing token naming where still valid** — the current `@theme` uses `--color-brand-*` and `--color-surface-*`. Extend, don't re-invent (add neutrals, chrome-rule tokens, type tokens with existing style).
- **AE-level acceptance examples** not used in origin brainstorm — tests reference R-IDs directly.

### External References

External research was skipped for this plan: tech stack is known (Tailwind v4 CSS-first custom properties, Astro 5 + CF Workers + Svelte 5 islands), the design.md spec was already examined during brainstorming, and no high-risk domains are touched. If the display-face comps at U7 raise licensing or OT-feature questions, research happens inside U7's iteration loop, not up-front.

---

## Key Technical Decisions

- **Fork, not template, on `google-labs-code/design.md`.** Revised 2026-04-23 post-review: the brainstorm's "fork" default stands. Fork preserves a visible GitHub upstream relationship (visible "forked from" badge in the UI), auto-inherits Apache 2.0 license (patent-grant clause that matches CBKDI's IP-aware posture elsewhere), and costs nothing — upstream-sync optionality is preserved at zero effort since no automated sync is planned either way. The earlier "template for clean history" rationale was weakly motivated; a template copy strips the visible lineage without material benefit.
- **CSS-first authoritative tokens.** `cbkdi/design-system/tokens.css` is the source of truth (Tailwind v4 `@theme` block). `DESIGN.md`'s YAML front-matter mirrors those values so `@google/design.md lint` and Claude Design still work, but CSS is authoritative. Dark mode expressed in the same file via `html.dark { ... }` overrides of custom properties — no parallel YAML token set. (Decided 2026-04-23 during brainstorm.)
- **Copy-with-commit-hash vendoring.** cbkdi-website vendors `tokens.css` as `src/styles/tokens.css` with a leading comment `/* Vendored from cbkdi/design-system@<sha> */`. No git submodule, no npm `file:` dep, no runtime external fetch. Refresh cadence is manual. Rationale: simplest mechanism that respects CSP; lowest carrying cost for a solo practice. Upgradeable later to a published npm package if CBKDI ever adopts a registry.
- **Route name: `/writing`.** Chosen over `/notes`, `/essays`, `/journal`. "Writing" signals substantive long-form without the diarist tone of "journal" or the implied brevity of "notes." Decision is soft and cheap to change later.
- **Dark mode is the authored-for mode.** All comps land dark-first during iteration. Default first-paint still respects `prefers-color-scheme` (no change from current behavior); authoring-for-dark is a design-process decision, not a runtime decision.
- **Strict single-accent purple, with a non-color differentiator for TOC-active state.** No second accent hue. Active-TOC state uses weight change or left-border indicator (decided in R8a).
- **`cbkdi/design-system` repo license: Apache 2.0** (inherited from upstream via fork). Rationale: includes explicit patent-grant clause (the substantive difference from MIT for a repo consumed by LLM tools and future agents); coherent with CBKDI's IP-aware posture in other artifacts (Hilltop retainer IP clause); fork inheritance means no separate license decision needed. Revised from MIT (earlier rationale) after doc-review.
- **DESIGN.md canonical sections** populated by CBKDI: Overview, Colors, Typography, Layout, Elevation & Depth (near-minimal — editorial-flat aesthetic does not use elevation heavily), Shapes (soft-cornered containers, hairline rules, §-anchors), Components (wordmark, breadcrumb, TOC, revision stamp, dark-card container, link), Do's and Don'ts.
- **Do NOT extract content in this refresh.** The repo research recommended folding the Phase 2 `src/data/` extraction into this work. Reconsidered: copy extraction adds a full round of touch-every-section edits that will fight with the 04-23 copy-pass edits happening in parallel. Sequence it after the copy pass lands so we're not editing the same strings twice. Tracked as a follow-up in Deferred to Follow-Up Work.
- **Interaction-states implementation uses Tailwind v4 state variants where possible** (`hover:`, `focus-visible:`, `aria-[current=page]:`, `data-[state=active]:`). Bespoke CSS only when a state cannot be expressed as a variant. Keeps the migration minimally invasive.

---

## Open Questions

### Resolved During Planning

- **Fork or template on `google-labs-code/design.md`?** → Template. (See Key Technical Decisions.)
- **Token distribution mechanism?** → Copy-with-commit-hash; vendor `tokens.css` into `cbkdi-website/src/styles/`. (See Key Technical Decisions.)
- **`/writing` route name?** → `/writing`. (See Key Technical Decisions.)
- **Default first-paint mode?** → Unchanged. Respects `prefers-color-scheme`; dark is authored-for but not defaulted-to.
- **New repo license?** → MIT.
- **Content extraction to `src/data/` — fold in or defer?** → Defer. Track as follow-up.

### Deferred to Implementation

- **Exact display serif face (attitude vs. discipline).** U7 iterates on real-copy comps with named candidates (GT Sectra, Fraunces, Migra, Beatrice Display, Editor's Note, Romie, Instrument Serif for attitude; Source Serif 4, Tiempos Headline, Equity Caps, GT Super for discipline). Choose per R13a-rubric-informed comparison on Hero + About + a /writing post mockup.
- **Exact monospace face.** U7. Evaluate Berkeley Mono (paid, distinctive) vs. free alternatives (JetBrains Mono, Geist Mono, IBM Plex Mono). Must ship with a specified fallback stack — first free option in the stack's second slot so font-load failure degrades gracefully.
- **Exact reading serif for `/writing` long-form body.** U7 or U11. Candidates: Source Serif 4, Tiempos Text, or stay with Inter. Decided after a real writing-layout comp.
- **Exact warm-near-black value for dark mode.** U3. Current `#111111` is slightly cool; pick a deliberate warm value (e.g., `#0f0e12`, `#121014`) with measured WCAG-AA contrast against body text `#e5e5e5` and purple `#a78bdb`.
- **Exact wordmark dot treatment.** U8. Keep leading dot (current), reposition to center-height inline, retire entirely, or replace with structural mark (em-rule, section sign, middle-dot). Decide alongside the display-face selection.
- **Exact sharpened positioning sentence.** U10. Iterate on candidates against exemplar-audience resonance; commit one before the Hero copy lands.
- **Exact list of tokens to extend the `@theme` block.** U3 authors the full set after reviewing design-audit.md + selected display/mono faces. Minimum scope: type scale (`--text-*`), neutral-gray scale (`--color-neutral-*`), rule colors (`--color-rule-*`), max-width, section padding, radii for dark-card containers, font-family stacks.
- **Whether the design-system repo ships a lightweight Astro-based gallery demo page** (live-render of components). Decide during U1 scaffold — lean toward no in v1 (DESIGN.md is sufficient for Claude Design consumption); add only if a concrete consumer need emerges.

### From 2026-04-23 doc review — integration status

The plan passed headless document review with 40+ findings across 6 personas. Safe-auto renumbering fixes were applied inline. A targeted deepening pass (2026-04-23) folded the major strategic findings into the unit definitions. **Integrated (no longer open):**

- ✅ **Fork + Apache 2.0** (Key Technical Decisions + U1 revised).
- ✅ **U8 chrome trimmed to v1 consumers** — `RevisionStamp` implemented; `Breadcrumb`, `Card`, `SectionAnchor` demoted to DESIGN.md spec only for future `/writing` build. `ThemeToggle`, Contact form, 404 page added to U8 scope.
- ✅ **U10 trimmed to DESIGN.md vocabulary spec** — no Astro scaffolding in v1. Astro files moved to Deferred to Follow-Up Work (U10 subsection).
- ✅ **Content extraction folded into U9** — `src/data/*.ts` modules authored as part of the copy pass; lands the Phase 2 prerequisite.
- ✅ **Positioning-sentence guidance sharpened** — verb-noun lead direction documented; Kreider-proxy resonance test added; earlier candidate called out as failing the same pattern it was meant to fix.
- ✅ **Tailwind v4 `@theme` pre-authoring verification step** — added to U2 approach.
- ✅ **Token scope expanded** — line-height per face, z-index scale, transition timing, focus-ring, error color, custom reading-breakpoint added to U2.
- ✅ **Active-TOC state committed** — `font-weight: 500` mechanism chosen (documented in U8 approach).
- ✅ **`/writing` sitemap + prerender clarified** — moot in v1 since no route exists until first-post effort.
- ✅ **U11 separated ship from integration claim** — cbkdi.com can ship; only external Claude Design claims are gated on the rubric.
- ✅ **Trace + renumbering errors** corrected (R1–R14 trace aligned to actual unit owners).

**Still open — implementer or user judgment required during `/ce-work`:**

**Scope-trim candidates (3 personas converged — scope-guardian, product-lens, adversarial):**

- [Affects U8, U10][User decision — scope] **Trim U8 chrome to v1 consumers only?** Of the 4 chrome components the plan creates (`Breadcrumb`, `RevisionStamp`, `Card`, `SectionAnchor`), only `RevisionStamp` has a v1 consumer on the public site. The others serve `/writing` which stays hidden until the first post. Leaner path: keep `RevisionStamp`, document the other three in DESIGN.md as component specs, defer their Astro-component implementation until `/writing` goes live. Saves ~30% of U8 effort.
- [Affects U10][User decision — scope] **Trim U10 to DESIGN.md spec only?** The plan builds `WritingLayout.astro`, `writing/index.astro`, `[slug].astro`, and `content/config.ts` for a route that stays hidden until the first real post — which the brainstorm defers to follow-up. Alternative: U10 specifies the `/writing` vocabulary **in DESIGN.md only** (layout sketch, reading-body face, TOC pattern, breadcrumb, revision stamp, footnote treatment). The Astro files are created as part of the future "first post" effort, not v1. Saves ~2–3 days of work, kills the polished-empty-orphan risk at the source, and puts the layout decisions alongside the first post's real content where they belong.

**Decision-reversals worth re-examining (2 personas — product-lens, adversarial):**

- [Affects R1, Key Decisions][User decision] **Fork vs. template — revisit.** The plan's Key Decisions flipped the brainstorm's "fork" default to "Use this template" with weak rationale. "Use this template" does not preserve a visible upstream relationship in GitHub's UI; the "credibility-via-fork-badge is weak" argument was asserted, not engaged. Fork also auto-inherits Apache 2.0 (patent grant), simplifying the license question below. **Recommendation: revert to fork.** Upstream-sync optionality is preserved at near-zero cost since no automated sync is planned either way.
- [Affects Key Decisions][User decision] **MIT vs. Apache 2.0 license.** Plan chose MIT; Apache 2.0 adds a patent-grant clause that matches CBKDI's IP-aware posture elsewhere (Hilltop retainer IP clause). If fork is chosen above, Apache 2.0 is inherited and this resolves automatically.
- [Affects U9, Key Decisions][User decision] **Content extraction to `src/data/` — fold into U9 after all?** Plan deferred it on the argument that it would "fight with" the copy pass. Product-lens argues the reasoning is inverted: U9 edits every section's copy, U5 edits every section's classes, and deferring extraction forces a third touch-every-section pass later. Better: U9 writes the new copy directly into `src/data/*.ts` typed modules as part of its edits, and section components import from there. Lands the Phase 2 prerequisite flagged in cbkdi-website's own CLAUDE.md.

**Technical verification required before U2 lands (feasibility + adversarial):**

- [Affects U2][Technical — blocker if wrong] **Verify Tailwind v4 `@theme` + `html.dark { --custom-prop: ... }` override pattern.** Tailwind v4's `@theme` inlines custom-property values into generated utilities by default. For `html.dark { --color-surface: ...; }` sibling-block overrides to propagate to utility classes like `bg-surface`, `@theme inline` syntax or explicit `var()` references may be required. Before authoring tokens.css, verify against Tailwind v4 docs that the plan's proposed structure ( `@theme { light defaults }` + sibling `html.dark { overrides }` ) actually generates dark-variant utilities correctly. If not, the CSS-first decision holds but the file structure changes (two declarations per token, or use Tailwind v4's `@theme inline` mode).
- [Affects U4][Technical] **Import order of `tokens.css` vs. `@import "tailwindcss"`.** Plan says tokens.css imports above tailwindcss; current global.css has tailwindcss first. Verify the Tailwind v4 Vite plugin picks up `@theme` and `@custom-variant` directives regardless of import order, or swap to match current pattern. Read Tailwind v4 docs before U4.

**Scope sequence + sequencing findings:**

- [Affects U5, U6][Sequencing] **U5 migrates type-scale tokens before U6 chooses faces** — font metrics may require re-migration if a chosen face shifts cap-height / line-height significantly. Mitigation: reserve U5-tail or U6-tail time to recheck `--text-*` values after face selection.
- [Affects U9, Key Decisions][Positioning] **Positioning sentence candidate still stacks generic words.** "Development intelligence for operators — sponsor-side real-estate discipline applied to the systems, processes, and products your business runs on" leads with a compound-noun brand phrase before the differentiator. Recommended direction: lead with the verb-noun of what actually gets done ("Turning ambiguous operator problems into durable systems that hold up in the room"), with the RE-discipline credential as a follow-on phrase. Test against Kreider — does "development intelligence" map to his problem? If no, rewrite.
- [Affects U11][Ship] **Separate "ship cbkdi.com refresh" from "publicize Claude Design integration."** U11's rubric gate only blocks external claims about the integration; the cbkdi.com refresh itself can ship on its own cadence. Already reflected in the revised U11 approach above.

**Token-set completeness (design-lens):**

- [Affects U2][Design] **Missing token categories in minimum scope.** Add: line-height tokens (per-face — display, body, mono each need distinct leading); shadow tokens (for dark-card containers if any elevation is intended — or explicitly state "no elevation, flat cards"); z-index scale (Header, TOC sidebar, ThemeToggle need to not collide); transition-timing tokens (otherwise chrome animations get inline magic numbers); focus-ring color token (currently accent-plus-opacity; value changes when warm-dark palette lands).
- [Affects U8][Design] **Commit the active-TOC-state mechanism.** R8a says "weight change or left-border indicator (non-color)" — pick one. Border requires padding budget in the TOC column; weight requires the chosen reading serif to ship a 500 weight. Decide before U10 builds `WritingLayout` — the markup differs.
- [Affects U5, U8][Design] **`ThemeToggle.svelte` + contact form + 404 page are not in migration scope.** ThemeToggle uses hardcoded Tailwind `slate-200` / `slate-700` defaults; contact form (high-stakes UX) has no specified error / loading / disabled states; `404.astro` is not in U5's file list. Fold into U5 (token migration) and U8 (interaction states).

**Font licensing + delivery (feasibility):**

- [Affects U6][Blocker risk] **Most display-serif candidates are paid foundry faces.** GT Sectra, Migra, Beatrice Display, Editor's Note, Romie, Tiempos Headline, Equity Caps, GT Super — all commercial licenses, not Google Fonts. Only Fraunces, Instrument Serif, Source Serif 4 are free in the candidate list. Plan flags licensing only for mono. Before U6 begins, narrow the candidate list based on licensing budget or confirm budget for paid faces (typical: $50–$300 per face per license tier).
- [Affects U6, Middleware][Technical] **Paid foundry fonts often require self-hosting or foundry-CDN origins.** Current CSP `font-src 'self' https://fonts.gstatic.com`. Self-hosting a webfont kit requires `public/fonts/` asset placement and `@font-face` rules (add to U6 Files); foundry CDNs require CSP `font-src` edits. Not currently accounted for in U6's Files list.

**Drift / sequencing — lower severity:**

- [Affects U4][Technical] **Copy-with-commit-hash vendoring has no drift check.** Add a minimal `scripts/refresh-tokens.sh` in cbkdi-website that does the copy + SHA update atomically, or a CI job that diffs the vendored file against the declared upstream SHA. Otherwise silent drift after first refresh.
- [Affects U5][Migration risk] **`[#hex]` grep-replace may collapse distinct semantic roles.** The same hex value (e.g., `#4a4a4a`) may carry different semantic meaning across Hero vs. Services vs. Footer. Before migration, grep + audit which hex literals carry the same value; decide whether each shared value is one token or multiple. Visual-parity check won't catch role-collision.
- [Affects U6][Budget] **Pre-clear a mono-licensing budget ceiling** (e.g., "up to $200 for a distinctive mono face") before U6 begins, to prevent mid-iteration stall on purchase decisions.
- [Affects U10][Build verification] **Test that `npm run build` completes with an empty Astro content collection.** Astro 5 + content-collection schema + empty MDX directory + `getStaticPaths: []` has version-sensitive behavior. Add to U10's test scenarios.

---

## Output Structure

The `cbkdi/design-system` repo is new. Target layout:

```
cbkdi/design-system/
├── README.md                    # what it is, how Claude Design consumes it, adoption path
├── DESIGN.md                    # YAML front-matter + canonical-section body
├── LICENSE                      # MIT
├── tokens.css                   # authoritative Tailwind v4 @theme block (light + dark overrides)
├── .github/
│   └── workflows/
│       └── lint.yml             # CI: npx @google/design.md lint DESIGN.md + WCAG checks
├── docs/
│   ├── brainstorms/             # move 2026-04-23-cbkdi-design-system-requirements.md here
│   │   └── 2026-04-23-cbkdi-design-system-requirements.md
│   └── plans/                   # move this plan file here on clone
│       └── 2026-04-23-001-feat-cbkdi-design-system-plan.md
└── examples/                    # optional — skip in v1 unless an adoption need emerges
```

Intent shape, not a constraint — the implementer may adjust (e.g., `tokens.css` could be split into `tokens.light.css` + `tokens.dark.css` if single-file becomes unwieldy).

cbkdi-website paths **touched or added** (not a full tree):

```
05 - Marketing/Website/cbkdi-website/
├── src/
│   ├── styles/
│   │   ├── tokens.css           # NEW — vendored from cbkdi/design-system
│   │   └── global.css           # @import "./tokens.css"; above Tailwind import; @theme moves to tokens.css
│   ├── components/
│   │   ├── layout/
│   │   │   ├── Header.astro     # wordmark refinement + /writing nav (behind flag until live)
│   │   │   └── Footer.astro     # tokenize hex-literals
│   │   └── sections/
│   │       ├── Hero.astro       # copy pass + tokenize + chrome
│   │       ├── About.astro      # copy pass + tokenize + chrome
│   │       ├── Services.astro   # copy pass + tokenize + chrome
│   │       ├── Engagement.astro # tokenize + chrome
│   │       ├── Contact.astro    # tokenize + chrome
│   │       └── Testimonials.astro # tokenize + chrome
│   ├── pages/
│   │   └── writing/
│   │       ├── index.astro      # NEW — /writing index, not linked from nav until first post
│   │       └── [slug].astro     # NEW — post template, scaffold only (no live posts)
│   └── layouts/
│       └── WritingLayout.astro  # NEW — long-form reading layout with chrome
└── docs/
    └── design-audit.md          # note pointer to cbkdi/design-system as new source of truth
```

---

## High-Level Technical Design

> *This illustrates the intended approach and is directional guidance for review, not implementation specification. The implementing agent should treat it as context, not code to reproduce.*

Token flow and consumer graph:

```mermaid
flowchart LR
    A[cbkdi/design-system<br/>public GitHub repo] -->|hand-authors| B[tokens.css<br/>Tailwind v4 @theme]
    A -->|hand-authors<br/>mirrors B| C[DESIGN.md<br/>YAML front-matter + body]
    C -.->|fetched + ingested| D[claude.ai/design]
    C -->|validated by| E[@google/design.md lint<br/>CI + local]
    B -->|copy-with-commit-hash| F[cbkdi-website<br/>src/styles/tokens.css]
    F -->|@import above<br/>tailwindcss import| G[cbkdi-website<br/>src/styles/global.css]
    G -->|consumed via<br/>utility classes| H[Section components<br/>Hero, About, etc.]
    G -->|consumed via<br/>utility classes| I[WritingLayout +<br/>post template]
    G -->|html.dark class<br/>selects dark tokens| J[Both modes, one CSS]
```

Content extraction (`src/data/`) is deliberately **not** on this graph — sequenced as a follow-up so it doesn't collide with the copy pass.

---

## Implementation Units

- [ ] U1. **Create `cbkdi/design-system` repo with scaffold**

**Goal:** Stand up the public `cbkdi/design-system` repo under the `cbkdi` GitHub org with the canonical file skeleton, so later units have a place to author. Uses "Use this template" on `google-labs-code/design.md`, then customizes.

**Requirements:** R1, R3, R4.

**Dependencies:** None (precondition check: `cbkdi` GitHub account has public-repo permission under `cbkdi` org — verify at clone time; scoped remote per `.claude/memory/reference_github_accounts.md`).

**Files:**
- Create (in new repo at first, then move to checkout path `05 - Marketing/design-system/`):
  - `README.md` — what it is, how Claude Design consumes it, adoption path
  - `DESIGN.md` — stubbed canonical sections (fill in U4)
  - `LICENSE` — MIT
  - `.github/workflows/lint.yml` — CI linting
  - `.gitignore` — node_modules, dist, local tooling caches
- Move:
  - `05 - Marketing/design-system/docs/brainstorms/2026-04-23-cbkdi-design-system-requirements.md` → preserved in new repo `docs/brainstorms/`
  - This plan (`docs/plans/2026-04-23-001-feat-cbkdi-design-system-plan.md`) → preserved in new repo `docs/plans/`

**Approach:**
- Fork `github.com/google-labs-code/design.md` under the `cbkdi` GitHub org as `cbkdi/design-system` (see Key Technical Decisions — revised to fork post-review).
- Set repo to public; enable Issues.
- Clone locally via scoped remote `https://cbkdi@github.com/cbkdi/design-system.git`; set local `user.email = conor@cbkdi.com`.
- **Set `com.dropbox.ignored` ADS on `node_modules/`, `dist/`, `.astro/` before first `npm install`** — the repo will live under Dropbox.
- **License: Apache 2.0 inherited from upstream** — confirm `LICENSE` exists and is unmodified from upstream at fork time. If the fork preserves upstream `NOTICE` or attribution files, preserve them verbatim.
- Customize the repo description and README to identify it as CBKDI's brand system (even though the fork relationship is visible in GitHub's UI via the "forked from" badge).
- Stub DESIGN.md with CBKDI-specific section headers only (replace upstream example content; U3 fills the body).

**Patterns to follow:**
- Scoped-remote pattern from `.claude/memory/reference_github_accounts.md`.

**Test scenarios:**
- *Verification path:* repo clones cleanly under the `cbkdi` account; `gh repo view cbkdi/design-system` confirms public + MIT license.
- *Verification path:* lint workflow stub runs on push and fails loudly (expected — DESIGN.md is not yet complete).

**Verification:**
- Repo exists at `github.com/cbkdi/design-system`, public, Apache 2.0 (inherited from fork of `google-labs-code/design.md`), "forked from" badge visible in GitHub UI.
- Brainstorm + this plan moved into the repo's `docs/` tree.
- Upstream `LICENSE` and any `NOTICE` file preserved verbatim.

---

- [ ] U2. **Author `tokens.css` — authoritative Tailwind v4 `@theme` block**

**Goal:** Write the full CBKDI token set as a single CSS file that serves as the source of truth for every consuming surface. Covers light + dark modes in one file via `html.dark { ... }` overrides of the same custom properties.

**Requirements:** R6, R7 (font-family stacks and type scale; exact faces deferred to U7), R14.

**Dependencies:** U1.

**Files:**
- Create: `tokens.css` (in `cbkdi/design-system`)

**Approach:**
- **Pre-authoring verification step (15 min):** Before writing tokens.css, verify two Tailwind v4 behaviors against the current Tailwind v4 docs: (a) whether `@theme` inlines custom-property values into generated utilities by default (requiring `@theme inline` mode or explicit `var()` references for runtime overrides), and (b) whether `html.dark { --custom-prop: ... }` as a sibling block actually propagates to Tailwind-generated utility classes. Doc review flagged this as potentially invalidating the CSS-first dark-mode structure. If verification shows the current plan's structure won't work, adjust to either `@theme inline` syntax or a pattern that uses Tailwind's dark-variant utility classes with token pairs (`bg-surface-light dark:bg-surface-dark`) rather than selector-based custom-property override. Either way, the CSS-first decision holds; only the mechanism inside the file may change.
- Start from `cbkdi-website/docs/design-audit.md`'s documented tokens (purple pair, neutrals, type `clamp()` scale, spacing, max-width, wordmark spec). Extend with:
  - **Color / surface:** Warm near-black dark surface (decide exact value with contrast check against `#e5e5e5` body and `#a78bdb` purple; shortlist `#0f0e12`, `#121014`, `#141218`). Neutral-gray scale tokens replacing the current `[#4a4a4a]` / `[#6e6e6e]` / `[#ddd]` / `[#2a2a2a]` / `[#aaa]` literals. Rule / hairline colors (`--color-rule-light`, `--color-rule-dark`). Dedicated `--color-focus-ring` token (decoupled from accent so warm-black palette shift doesn't break focus ring). Dedicated `--color-error` token for contact-form error state (not browser default red).
  - **Shape:** Container + chrome radii — commit `--radius-card: 0.75rem` (12px) now. `--radius-pill` for button / toggle shapes if any. No shadow tokens (editorial-flat aesthetic — explicitly stated in DESIGN.md Elevation & Depth section as deliberate minimal).
  - **Layout:** Max content width (`66rem` confirmed). Section padding scale as named tokens. `--breakpoint-reading` = `1080px` (custom breakpoint above content-max, used for `/writing` TOC sidebar — avoids Tailwind `lg` (1024px) dead zone flagged in doc review).
  - **z-index:** `--z-header`, `--z-toc-sidebar`, `--z-theme-toggle`, `--z-modal`, `--z-toast` scale so stacking is coordinated, not ad-hoc.
  - **Type:** Type-family stacks — `--font-display`, `--font-body`, `--font-mono`. Leave face names as placeholders until U6 finalizes. Type-scale tokens `--text-eyebrow`, `--text-body`, `--text-small`, `--text-section-head`, `--text-hero` mapping to the audit's `clamp()` values. Reading-long-form variants `--text-reading-base`, `--text-reading-h2`, `--text-reading-h3` for `/writing` (authored in U10, but token names reserved now). **Line-height tokens per face:** `--leading-display` (~1.1), `--leading-body` (~1.6), `--leading-mono` (~1.45), `--leading-reading` (~1.7) — different faces need different vertical rhythm.
  - **Motion:** Transition-timing tokens `--duration-fast` (150ms), `--duration-normal` (250ms), `--ease-standard` (ease-out cubic-bezier). All chrome animations use these; all gated behind `@media (prefers-reduced-motion: no-preference)` at usage sites.
- **Dark-mode structure in tokens.css** (subject to the pre-authoring verification above): preserve the existing pattern of *two distinct tokens* per light/dark where it makes sense (`--color-surface-light` / `--color-surface-dark`) paired with Tailwind `dark:` variants, rather than a single-token override. This is what the current codebase already does and what Tailwind v4's docs model cleanly. The earlier plan's "one token, `html.dark` overrides" approach is the riskier path and should only be adopted if verification confirms it works with Tailwind v4's `@theme` mode.
- Preserve existing brand-\*-50…950 scale; extend where tokens are missing.
- Run `@google/design.md lint` locally against the DESIGN.md-YAML-mirror (written in U3) to verify contrast rules pass.

**Execution note:** Characterization-first. Before changing any cbkdi-website section code (U6), confirm the tokens render identically at representative sections via side-by-side snapshots at parity.

**Patterns to follow:**
- Current `@theme` in `05 - Marketing/Website/cbkdi-website/src/styles/global.css` — same block style, same custom-variant pattern.
- `@custom-variant dark (&:where(.dark, .dark *))` preserved verbatim.

**Test scenarios:**
- *Happy path:* WCAG AA contrast passes for every documented body-on-surface and accent-on-surface pairing in both modes (manual check via Stark or `@google/design.md lint`).
- *Edge case:* Dark warm-black value has contrast ≥ 4.5:1 against body text `#e5e5e5` and ≥ 3:1 against purple `#a78bdb` at heading sizes.
- *Integration:* When `tokens.css` is vendored into cbkdi-website (U5) and `global.css` is rewritten to import it, Hero + Services + Engagement + Contact sections render **visually identical** (or an intentional delta the U6 comps approve) compared to the pre-vendor baseline — proves the tokens faithfully cover current usage.

**Verification:**
- `tokens.css` loads standalone in a one-page test doc with representative CBKDI markup (hero headline, section heading, body para, mono caption) and renders correctly in both modes.
- Lint passes once U4's YAML mirror is authored.

---

- [ ] U3. **Author `DESIGN.md` v1 — YAML front-matter + canonical body + blurb + rubric + 02ui moves**

**Goal:** Write the DESIGN.md that Claude Design consumes and that an implementer / contractor reads to understand the brand. YAML front-matter mirrors `tokens.css` exactly; markdown body explains intent.

**Requirements:** R2, R3, R4, R5, R5a, R7, R8, R8a, R13, R13a.

**Dependencies:** U1, U2.

**Files:**
- Create: `DESIGN.md` (replacing the stub from U1)

**Approach:**
- **YAML front-matter** — mirror every value from `tokens.css` as canonical design.md tokens (colors, typography, spacing, shape, components). Use a parallel naming convention for light vs. dark (e.g., `colors.bg-light` / `colors.bg-dark`) as recommended by the brainstorm's RBP resolution — not because the spec requires it but because the linter's contrast-ratio rule checks one palette at a time. Exact shape TBD on first lint pass.
- **Canonical section body** — populate: Overview (what CBKDI is + intake blurb from R13), Colors (palette rationale + purple single-accent), Typography (three-face system with roles), Layout (container + section rhythm), Elevation & Depth (near-empty; editorial-flat aesthetic, note this as a deliberate minimal), Shapes (soft-cornered dark-card containers, hairlines, §-anchors), Components (wordmark, breadcrumb, TOC, revision stamp, dark-card container, link, button), Do's and Don'ts.
- **Enumerated "02ui moves borrowed"** — per R5a, a concrete list in the Shapes or Components section of the specific moves CBKDI takes from 02ui.com, translated away from pixel-art. E.g.: three-face type system with mono structural chrome; hot-accent-on-warm-dark palette; soft-cornered dark-card containers; uppercase + tracked mono labels; breadcrumb / TOC / revision-stamp chrome; specific type-contrast register; sparing §-anchor use.
- **Claude Design intake blurb** (R13) — v0.1 draft from Key Decisions lands here; revised per U9's positioning-sharpening outcome (see U3 Execution note below).
- **R13a rubric** — the concrete pass/fail criteria for "visibly, unmistakably CBKDI" embedded in the Do's and Don'ts section, framed as a testable rubric for anyone (including Claude Design output reviewers) to apply.

**Execution note:** Iterate. This file will change as U6 (faces) and U9 (copy / positioning sentence) resolve. Land a v0.1 here; re-visit once faces are selected in U6; re-visit blurb + body after U9 commits the positioning sentence; re-visit finally at U11's lint + rubric-gate pass.

**Patterns to follow:**
- `google-labs-code/design.md`'s own DESIGN.md as shape reference (but not CBKDI's content).

**Test scenarios:**
- *Happy path:* `npx @google/design.md lint DESIGN.md` passes with zero errors.
- *Edge case:* Lint's WCAG AA contrast rule passes for all documented `textColor`/`backgroundColor` component pairs in both mode palettes.
- *Integration:* Section headers conform to the canonical order required by the spec (Overview, Colors, Typography, Layout, Elevation & Depth, Shapes, Components, Do's and Don'ts) — otherwise the structural lint rule fails.
- *Edge case:* YAML front-matter references only tokens defined elsewhere in the file — no broken token references (lint rule).
- *Happy path (R13a rubric applicable):* The rubric section is explicit enough that an independent reader could apply it to a third-party screenshot and reach the same pass/fail verdict.

**Verification:**
- Lint passes locally and in CI (the workflow stub from U1 now turns green).
- A new reader (or Claude Design) can read DESIGN.md alone and understand: what CBKDI is, the three-face system, the single-accent rule, the chrome vocabulary, and what good output looks like.

---

- [ ] U4. **Vendor `tokens.css` into `cbkdi-website`**

**Goal:** Pull the authoritative `tokens.css` from `cbkdi/design-system` into `cbkdi-website`, remove the current inline `@theme` block, and wire the import chain so Tailwind v4 picks up the vendored tokens without runtime fetching.

**Requirements:** R12, R14.

**Dependencies:** U2 (tokens exist); U3 nice-to-have (lint green) but not strictly required for vendoring.

**Files:**
- Create: `05 - Marketing/Website/cbkdi-website/src/styles/tokens.css` (vendored copy)
- Modify: `05 - Marketing/Website/cbkdi-website/src/styles/global.css` (remove `@theme` block; add `@import "./tokens.css";` above the `@import "tailwindcss"` line)
- Modify: `05 - Marketing/Website/cbkdi-website/CLAUDE.md` (note that `tokens.css` is vendored from `cbkdi/design-system` and how to refresh it)

**Approach:**
- Copy `tokens.css` from the design-system repo at a specific commit hash.
- Prepend `/* Vendored from cbkdi/design-system@<short-sha> on <YYYY-MM-DD>. Source of truth: https://github.com/cbkdi/design-system. Refresh: copy verbatim; do not edit in place. */`.
- Move the `@custom-variant dark` declaration from `global.css` into `tokens.css` (keeps the dark-variant registration co-located with the dark-mode token overrides).
- Retain the `::selection` and `:focus-visible` rules in `global.css` (they're site-specific, not brand-wide — for now).
- Update `cbkdi-website/CLAUDE.md` § "Phase 2 prerequisite" to add a § "Design system vendoring": how to refresh `tokens.css`, who owns source of truth, and the do-not-edit-in-place rule.

**Patterns to follow:**
- Existing `global.css` structure at `05 - Marketing/Website/cbkdi-website/src/styles/global.css`.

**Test scenarios:**
- *Happy path:* `npm run build` from cbkdi-website succeeds; no unresolved token-name errors from Tailwind v4.
- *Happy path:* Rendered site (local dev) shows identical visuals to pre-vendor baseline at Hero, Services cards, Engagement flow — tokens cover everything currently used. Any intentional deltas (warm-black surface, new neutrals) are review-approved before U6 starts.
- *Integration:* CSP middleware continues to serve `style-src 'self' 'unsafe-inline' https://fonts.googleapis.com` — no new origins; tokens are same-origin.
- *Edge case:* Dark-mode toggle still functions (ThemeToggle.svelte unchanged); `html.dark` selector in vendored `tokens.css` applies correctly.

**Verification:**
- Site builds clean, renders clean, dark mode still works, no CSP violations in browser console.

---

- [ ] U5. **Migrate cbkdi-website section components from `[#hex]` literals to tokens**

**Goal:** Replace all `text-[#hex]` / `bg-[#hex]` / `border-[#hex]` / `text-[clamp(...)]` arbitrary-value utilities across the six section components + Header + Footer + Navigation with token utilities. No visual change beyond token alignment; this unit is the mechanical cleanup that unblocks U6's visual refresh.

**Requirements:** R5 (enabling), R6 (applied uniformly), R14 (no duplicate definitions — the `[#hex]` literals are duplications).

**Dependencies:** U4.

**Files:**
- Modify:
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Hero.astro`
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/About.astro`
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Services.astro`
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Engagement.astro`
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Contact.astro`
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Testimonials.astro`
  - `05 - Marketing/Website/cbkdi-website/src/components/layout/Header.astro`
  - `05 - Marketing/Website/cbkdi-website/src/components/layout/Footer.astro`
  - `05 - Marketing/Website/cbkdi-website/src/components/layout/Navigation.astro`

**Approach:**
- Grep for `\[#[0-9a-f]{3,6}\]` and `text-\[clamp\(` patterns; replace with the new token utilities.
- Preserve the existing brand-700/brand-400 light/dark accent pairing (the only "tokenized" relationship today — keep it).
- Preserve semantic HTML (section ids, aria-labelledby, role attributes).
- Do **not** change copy in this unit. Copy pass is U10.

**Execution note:** Characterization-first. Capture before/after screenshots of each section in light + dark modes; confirm visual parity (or intentional deltas) before the next unit starts work on top of this one.

**Patterns to follow:**
- Existing token usage (e.g., `text-brand-700 dark:text-brand-400`) — extend to neutrals.

**Test scenarios:**
- *Happy path:* All nine files compile; `npm run build` succeeds.
- *Happy path:* Rendered Hero, About, Services, Engagement, Contact in both modes match the pre-migration baseline pixel-for-pixel (or deltas match the approved list from U2).
- *Edge case:* No `[#hex]` or `[clamp(]` patterns remain in any of the nine files (grep returns empty).
- *Integration:* CSP posture unchanged; middleware-injected nonces still work; Umami analytics still fires.
- *Edge case:* Dark-mode toggle instantly flips every migrated surface without leftover light-mode colors bleeding through.

**Verification:**
- `rg '\[#[0-9a-f]{3,6}\]' src/components/` returns zero hits.
- `rg 'text-\[clamp' src/components/` returns zero hits (all clamp values now live as `--text-*` tokens).
- Dark-mode flip is instant and complete at every migrated section.

---

- [x] U6. **Select display serif, reading serif (for /writing), and monospace faces through real-copy comps**

**Goal:** Resolve the three-face system's actual face choices via iteration on real CBKDI copy, informed by the R13a rubric. Produces a final `--font-display`, `--font-body` (plus optional reading-serif override for /writing), and `--font-mono` commitment.

**Requirements:** R7.

**Dependencies:** U2 (tokens exist with face placeholders), U5 (section components token-ready — so comps render against real layout).

**Files:**
- Modify: `tokens.css` (in `cbkdi/design-system`) — swap font-family placeholders to chosen faces
- Modify: `05 - Marketing/Website/cbkdi-website/src/styles/tokens.css` (re-vendor)
- Modify: `05 - Marketing/Website/cbkdi-website/src/layouts/BaseLayout.astro` — add `<link>` preconnects and font imports for the chosen faces (Google Fonts URL, or self-hosted paths if any face is self-hosted)
- Modify: `cbkdi/design-system/DESIGN.md` — Typography section reflects chosen faces

**Approach:**
- **Display candidates (attitude):** GT Sectra, Fraunces (high-contrast axis), Migra, Beatrice Display, Editor's Note, Romie, Instrument Serif.
- **Display candidates (disciplined):** Source Serif 4, Tiempos Headline, Equity Caps, GT Super.
- **Reading-body candidate (/writing):** Source Serif 4, Tiempos Text, or stay with Inter (reject-reading-serif option).
- **Monospace candidates:** Berkeley Mono (paid), JetBrains Mono, Geist Mono, IBM Plex Mono. **Fallback stack must include at least one free option as the second slot.**
- **Iteration process:** Build three comps — Hero, About, and a representative /writing post mockup — with each candidate combination (narrow list before rendering — don't render all combinations). Apply the R13a rubric to each. Review side-by-side against the prior Newsreader attempt to confirm this direction feels different (not a premium-restraint re-run).
- **Licensing check:** Confirm any paid face's license covers CBKDI's current + foreseeable usage (website + DESIGN.md consumption). If Berkeley Mono is selected, budget and acquire before finalizing.
- **Commit once rubric passes:** First combination that passes all R13a must-haves + 3 of 5 should-haves + no must-not-haves is a candidate; compare top candidates on subjective "do I want to publish on this?" gut check; commit.

**Execution note:** This is iterative creative work, not build-fix-ship. Expect 2–4 rounds of comps. Plan 1–3 working days.

**Patterns to follow:**
- Real-copy comps per prior Newsreader-rejection learning (don't evaluate on lorem ipsum).
- Google Fonts preconnect pattern already in `BaseLayout.astro`.

**Test scenarios:**
- *Verification path (rubric-gated):* Each rendered comp passes the R13a rubric (must-haves + 3 of 5 should-haves + no must-not-haves).
- *Edge case:* Font-load failure in browser degrades gracefully to the specified fallback stack; no Courier New, no default serif.
- *Integration:* Chosen faces render consistently in Chrome, Safari, Firefox; no OpenType feature breakage on variable fonts.
- *Edge case:* Fonts do not inflate CSP — either same-origin or `fonts.googleapis.com`/`fonts.gstatic.com` already allowed.

**Verification:**
- `tokens.css` has three committed font-family values + fallback stacks.
- DESIGN.md Typography section names the faces with rationale.
- `BaseLayout.astro` loads the fonts correctly (preconnect + font-face).
- A reviewer can look at a Hero comp in dark mode and identify the three faces in play.

---

- [x] U7. **Refine the wordmark (dot treatment + display-face integration)**

**Goal:** Finalize the `• CBKDI` wordmark — keep the leading purple dot, reposition, retire, or replace with a structural mark. Decision coordinates with the chosen display face from U6.

**Requirements:** R9.

**Dependencies:** U6 (display face chosen — wordmark design depends on the face's character).

**Files:**
- Modify: `05 - Marketing/Website/cbkdi-website/src/components/layout/Header.astro` (wordmark markup at lines 15–18)
- Optionally Modify: `05 - Marketing/Website/cbkdi-website/src/components/layout/Footer.astro` (add wordmark if decision is to unify header+footer identity)
- Modify: `cbkdi/design-system/DESIGN.md` — Components section documents the wordmark spec (markup, sizing, dot treatment, tracking, weight)

**Approach:**
- Evaluate candidate treatments against the chosen display face:
  - Keep leading dot (current): `• CBKDI` — works if display is restrained.
  - Inline mid-height dot: `CBKDI·` — reads as punctuation, more editorial.
  - No dot, typographic only: `CBKDI` — tightest.
  - Em-rule: `CBK—DI` — structural.
  - Section sign: `§CBKDI` — heavy-handed; probably not.
  - Middle-dot: `C·B·K·D·I` — tracked editorial feel; risky, depends on face.
- Pick one, prototype in Header.astro, review in both modes.
- Encode in DESIGN.md Components section with exact markup.

**Patterns to follow:**
- Current wordmark implementation (`Header.astro:15–18`) as the structural starting point — span-with-rounded-full-dot is portable.
- `aria-hidden="true"` on the dot element for screen readers.

**Test scenarios:**
- *Happy path:* Wordmark renders correctly in light + dark at the header's current size.
- *Edge case:* Wordmark scales legibly at 24px (smaller utility contexts, e.g., future email signature) and 72px (hero-adjacent usage if any).
- *Edge case:* Dot (if kept) aligns vertically with cap-height text at the chosen display face's specific metrics — no drift at different sizes.
- *Integration:* Screen-reader announces "CBKDI" (dot is aria-hidden); the purple dot is decorative-only.

**Verification:**
- Wordmark looks intentional against the chosen display face, in both modes.
- DESIGN.md Components.wordmark spec is precise enough that an implementer could rebuild it without access to Header.astro.

---

- [ ] U8. **Implement v1 chrome (RevisionStamp) + interaction states for existing interactive elements**

**Goal:** Build the one chrome component that has a v1 consumer on the public site (`RevisionStamp`, inserted on every page) and pin interaction states for every existing interactive element (nav, links, contact form fields, ThemeToggle). Revised 2026-04-23 post-review: `Breadcrumb`, `Card`, and `SectionAnchor` serve only the `/writing` surface — their specs live in DESIGN.md (U3) and their Astro-component implementations ship with the first real post, not in v1.

**Requirements:** R5, R8 (component specs in DESIGN.md via U3; RevisionStamp implementation here), R8a.

**Dependencies:** U5 (tokens available), U6 (mono face chosen — RevisionStamp is mono).

**Files:**
- Create: `05 - Marketing/Website/cbkdi-website/src/components/ui/RevisionStamp.astro` — page-foot date stamp in mono; the one v1 chrome consumer.
- Modify: `05 - Marketing/Website/cbkdi-website/src/layouts/BaseLayout.astro` or `PageLayout.astro` — insert `<RevisionStamp />` in the page foot (source: front-matter `lastmod` or git commit date).
- Modify: `05 - Marketing/Website/cbkdi-website/src/components/layout/ThemeToggle.svelte` — replace hardcoded `hover:bg-slate-200 dark:hover:bg-slate-700` with brand-token-driven hover states (uses the new neutral-gray tokens from U2, not Tailwind defaults).
- Modify: `05 - Marketing/Website/cbkdi-website/src/components/sections/Contact.astro` — specify field focus / error / disabled states and submit-button loading / success / error states using brand tokens. Error state uses a dedicated `--color-error` token (add to U2 if not already) rather than browser default red.
- Modify: `05 - Marketing/Website/cbkdi-website/src/pages/404.astro` — token migration + interaction-state alignment with the rest of the site (caught in doc review; not in U5's scope).
- Modify: `cbkdi/design-system/DESIGN.md` Components section — document all chrome components (RevisionStamp implementation-ready; Breadcrumb, Card, SectionAnchor as component-specs ready for future `/writing` build).
- Modify: `tokens.css` — add state-specific tokens as they emerge: `--color-focus-ring` (decoupled from accent so warm-black palette shift doesn't break focus ring), `--color-error` (for form error state), transition-timing tokens (`--duration-fast`, `--duration-normal`), line-height tokens per face (`--leading-display`, `--leading-body`, `--leading-mono`).

**Approach:**
- **RevisionStamp** (the one v1 implementation): small mono caption at the page foot (`REV YYYY.MM` or `Updated YYYY-MM-DD`). Tracked uppercase. Source: page front-matter `lastmod` field if present, else git commit date of the page file.
- **Component specs authored in DESIGN.md (implementation deferred):**
  - **Breadcrumb:** `<nav aria-label="breadcrumb">` with `<ol>` > `<li>` > `<a>`; separator is a mono `/`; last item `<span aria-current="page">`. Truncation strategy for long titles: middle-segment ellipsis at ≤ 40ch. (Will be implemented alongside the first `/writing` post.)
  - **Card:** `class="bg-surface-card-light dark:bg-surface-card-dark rounded-card"` pattern; `--radius-card` = `0.75rem` (12px — commit this value). Padding token-driven. No elevation (flat cards — editorial-flat aesthetic; no shadow tokens needed).
  - **SectionAnchor:** `<span>` with `id` and inline `§NN` label in mono, rendered alongside `h2`/`h3`. Used sparingly on long-form.
- **Existing-element interaction states (R8a — implemented in v1 on existing surfaces):**
  - Nav link (Header): default → hover (token underline) → focus-visible (purple outline, `outline-offset: 3px`) → current-page (non-color: underline or weight).
  - Body link (in section prose): same pattern minus current-page.
  - Contact-form field: default → focus (accent ring) → error (dedicated `--color-error` token + inline message) → disabled (opacity token).
  - Contact-form submit button: default → hover → focus-visible → loading (disabled + text swap) → success (confirmation UI) → error (inline message).
  - ThemeToggle: default → hover (`hover:bg-[var(--color-neutral-200)] dark:hover:bg-[var(--color-neutral-800)]` — token-driven, replacing the current `slate-*` defaults) → focus-visible.
- **Active-TOC-state mechanism (commit now for DESIGN.md doc):** `font-weight: 500` on active item. Rationale: no layout-budget change (border-left-2 requires column padding budget); every candidate body/display face ships a 500 weight; cleaner on mobile. Documented in DESIGN.md Components.TOC for future implementation.
- **Reduced motion:** all transitions gated behind `@media (prefers-reduced-motion: no-preference)`.

**Patterns to follow:**
- Current `:focus-visible` outline rule at `global.css:53-61` — carry forward with token-driven color.
- Existing accent-ring pattern.

**Test scenarios:**
- *Happy path:* Each state renders visually correctly for each chrome element in both modes (manual visual + screen-reader audit).
- *Edge case:* Focus-visible ring is visible in dark mode (purple `#a78bdb` on warm dark).
- *Edge case:* `prefers-reduced-motion: reduce` disables all chrome transitions.
- *Integration:* Keyboard navigation works through nav, breadcrumb, card (if clickable), and any interactive chrome in a predictable tab order.
- *Error path:* Disabled states do not appear focusable (`aria-disabled="true"`, `tabindex="-1"`).
- *Integration:* Screen reader announces breadcrumb current page correctly (`aria-current="page"` on last `<li>`).

**Verification:**
- Components directory has the four new UI components; each one has a documented spec in DESIGN.md.
- Manual keyboard-nav walkthrough (Tab / Shift+Tab / Enter) works through every interactive chrome element without focus-trap or invisible-focus bugs.
- Reduced-motion preference is respected.

---

- [ ] U9. **Copy pass + content extraction to `src/data/`: sharpen positioning, align Hero/About/Work/blurb, land the Phase 2 prerequisite**

**Goal:** Revised 2026-04-23 post-review: combine the copy pass (04-23 positioning refinement) with the content extraction to `src/data/` that cbkdi-website's own `CLAUDE.md` names as a live Phase 2 prerequisite. The extraction and the copy pass both touch every section — doing them in one pass is cheaper than the two-pass sequence the plan originally proposed. Produces: sharpened single-sentence positioning, revised Hero/About/The Work copy, aligned Claude Design intake blurb, and section copy moved from inline JSX/consts to typed `src/data/*.ts` modules.

**Requirements:** R10 (ship unit: copy + visuals together), R13 (blurb mirrors positioning), R5 (voice preservation). Also lands Phase 2 prereq flagged in cbkdi-website/CLAUDE.md.

**Dependencies:** None blocking for the copy work itself (can draft in parallel with U2–U8). The `src/data/` extraction should happen during this unit rather than being sequenced later.

**Files:**
- Create: `05 - Marketing/Website/cbkdi-website/src/data/site.ts` — typed exports for nav items, footer links, brand name variants (CBKDI / CBK Development Intelligence), contact address.
- Create: `05 - Marketing/Website/cbkdi-website/src/data/hero.ts` — headline, subhead, call-to-action text.
- Create: `05 - Marketing/Website/cbkdi-website/src/data/about.ts` — bio paragraphs, credentials, meta-grid fields.
- Create: `05 - Marketing/Website/cbkdi-website/src/data/work.ts` — section heading, description paragraph, capabilities list, "In the Room" tags.
- Create: `05 - Marketing/Website/cbkdi-website/src/data/engagement.ts` — step titles, step descriptions, section heading.
- Create: `05 - Marketing/Website/cbkdi-website/src/data/contact.ts` — section heading, email, brief-grid fields.
- Create: `05 - Marketing/Website/cbkdi-website/src/data/testimonials.ts` — if testimonials render in v1 (currently present — confirm).
- Modify:
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Hero.astro` — import from `src/data/hero.ts`; no inline copy.
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/About.astro` — import from `src/data/about.ts`.
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Services.astro` — import from `src/data/work.ts`.
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Engagement.astro` — import from `src/data/engagement.ts`.
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Contact.astro` — import from `src/data/contact.ts`.
  - `05 - Marketing/Website/cbkdi-website/src/components/sections/Testimonials.astro` — import from `src/data/testimonials.ts`.
  - `05 - Marketing/Website/cbkdi-website/src/components/layout/Header.astro` — nav items read from `src/data/site.ts`.
- Modify: `cbkdi/design-system/DESIGN.md` — R13 intake blurb section reflects the sharpened positioning (first line mirrors the committed positioning sentence exactly).
- Modify: `05 - Marketing/Website/cbkdi-website/ROADMAP.md` — mark the content-extraction prerequisite as complete (Phase 2 unblocked for future work).
- Modify: `05 - Marketing/Website/cbkdi-website/CLAUDE.md` — update the "Phase 2 prerequisite" section to note it's landed.

**Approach:**
- **Draft 3–5 candidate single-sentence positioning lines. Lead with the verb-noun of what actually gets done, not with a branded noun-phrase.** The earlier brainstorm starting direction ("Development intelligence for operators — sponsor-side real-estate discipline applied to the systems, processes, and products your business runs on") was flagged in doc review as still stacking generic practice words before the differentiator. Better shapes to iterate:
  - "Turning ambiguous operator problems into systems that hold up in the room — drawing on 15 years of sponsor-side real-estate development."
  - "I help operators build the systems, processes, and products their businesses run on — with the judgment of someone who has sat on every side of a real-estate deal."
  - "Sponsor-side development discipline, applied to the operating systems of ambitious businesses."
  - These are **directions to iterate**, not finalists. Test each: if the sentence read aloud to a Kreider-type construction owner prompts the response "yes, that's exactly my problem," it's landing. If the response is "I'm not sure what that means for me" or "that sounds like a consultant," it's not.
- **Kreider-proxy resonance check as a named test step.** Read each candidate to a proxy for the construction-owner audience (an actual Kreider-type operator if available, else Conor imagining Greg Kreider reading it). "Development intelligence" is likely to fail this test because it reads as real-estate-developer-speak; sentences that lead with "ambiguous operator problems," "systems that hold up," or "the operating systems your business runs on" are more likely to map to his world. Same check for Steve (RE sponsor — does he see deal underwriting reflected?) and Erich (first-time platform-builder — does he see the platform problem?).
- **Hero:** headline + sub-head. Consider whether "Senior judgment. Durable systems." survives (likely yes) or gets replaced with the chosen positioning sentence.
- **About:** lift the UEB Builders systems-engineering bit — evidence that judgment + systems-building have been intertwined in Conor's career, not sequential. Do not over-add; preserve conciseness.
- **The Work section heading + description:** broaden from "what has to be true for this deal" to language encompassing systems/process/product work without enumerating audiences. The section heading may or may not change; the description paragraph needs refresh.
- **The Work capabilities list:** rewrite all 6 items at the level of abstraction where every line works for sponsor, platform-builder, and construction-owner reads. No audience naming. No GC-specific or RE-specific jargon.
- **Engagement steps:** generalize "Build or repair the core underwriting" and "Models, memos, and framework" so the 4-step sequence fits systems / process engagements equally.
- **Intake blurb (R13 in DESIGN.md):** mirror the chosen positioning sentence exactly in the first line; drop trailing "Fractional development leadership is available…" clause or demote further.
- **Voice:** first-person (I/my) throughout; no em dashes in client-facing copy (hyphen only per `CLAUDE.md`).

**Patterns to follow:**
- 2026-03-23 messaging brainstorm at `05 - Marketing/Website/cbkdi-website/docs/brainstorms/2026-03-23-messaging-evolution-requirements.md` — the requirements hold; this is the follow-on pass.
- `.claude/memory/feedback_website_copy.md` — broaden through general language, don't get GC-specific.
- `.claude/memory/project_cbkdi_positioning.md` — the 04-23 positioning memo is authoritative.

**Test scenarios:**
- *Verification path (audience resonance):* Draft positioning sentence — read aloud, ask "does a Steve-type / Erich-type / Kreider-type reader see their problem here?" for each. All three must pass.
- *Verification path (voice):* No em dashes in any Hero/About/Work/Engagement/Contact string. No third-person "CBKDI does X" constructions in client-facing copy.
- *Verification path (anti-regression):* The word "Fractional" does not appear in the Hero. "Development Lead" is not the primary credential. The three-exemplar structure does not read as "three service lanes."
- *Integration:* DESIGN.md's R13 intake blurb matches the committed Hero sentence — no drift.

**Verification:**
- A first-time reader lands on the refreshed site and answers "what does CBKDI do?" with some form of systems/process/product design for operators (not "fractional development lead").
- Success Criterion #2 from the brainstorm passes: the three exemplar audiences each see their own problem; none feels like "the target."

---

- [x] U10. **Document `/writing` layout vocabulary in DESIGN.md (no Astro scaffolding in v1)**

**Goal:** Revised 2026-04-23 post-review: rather than building `WritingLayout`, `writing/index.astro`, `[slug].astro`, and `content/config.ts` ahead of any publishing cadence, U10 specifies the full `/writing` vocabulary in `cbkdi/design-system/DESIGN.md`. Astro files are created alongside the first real post — the effort that has real content to shape the layout against. Eliminates the polished-empty-orphan risk at source.

**Requirements:** R11 (vocabulary specified in v1; Astro scaffold deferred).

**Dependencies:** U3 (DESIGN.md authored), U6 (faces chosen — reading-body face decision needs to land here for the spec).

**Files:**
- Modify: `cbkdi/design-system/DESIGN.md` — expand the Typography and Layout sections to cover `/writing` long-form reading:
  - Reading-body face commitment (Source Serif 4 / Tiempos Text / stay with Inter — decided in U6).
  - Long-form type scale: `--text-reading-base`, `--text-reading-h2`, `--text-reading-h3` with distinct `clamp()` values tuned for reading measure.
  - Reading column measure: max-width in `ch` or `rem` for optimal line length (~66ch is a defensible starting point).
  - Line-height for reading body (typically 1.6–1.75, larger than UI body).
  - TOC pattern (sidebar ≥ 1080px / collapsible drawer < 1080px — breakpoint chosen above content-max of 1056px to avoid the 1024–1056px dead zone the doc review flagged).
  - Active-TOC state: `font-weight: 500` on current item (committed in U8 approach).
  - Breadcrumb pattern + truncation rule (middle-segment ellipsis at ≤ 40ch).
  - Revision-stamp placement on long-form posts.
  - Footnote typography + numbering pattern (mono numerals per 02ui moves borrowed, per R5a).

**Approach:**
- This is a documentation unit, not a build unit. Think of the output as: "an implementer building the first `/writing` post can read DESIGN.md alone and know exactly what to build."
- No Astro files created in this unit. No content collection config. No live route.
- The nav items array in `Header.astro` stays untouched (no `/writing` nav entry).
- Sitemap and `robots.txt` exclusion is moot in v1 — there is no `/writing` URL to exclude because the route doesn't exist yet.

**Patterns to follow:**
- Reference 02ui.com's long-form post layout as the visible target (screenshot captured under U3's R5a enumerated moves).
- Reference Ink & Switch's long-form essay pages as a secondary target for reading measure and typography.

**Test scenarios:**
- *Verification path:* A third-party reader (or Conor 6 months later) can read DESIGN.md's Typography + Layout + Components sections and describe the full `/writing` reading experience without access to any Astro files.
- *Verification path:* `@google/design.md lint` passes with the expanded content (no broken token references in the new reading-layout sections).
- *Edge case:* The 1080px TOC breakpoint in the spec avoids the 1024–1056px "both sidebar and compressed column" dead zone; DESIGN.md notes why this breakpoint is chosen (not Tailwind's default `lg`).

**Verification:**
- DESIGN.md has a named subsection (under Layout or Components) that fully specifies `/writing` reading layout.
- When the first post effort begins, no new design decisions are required — only implementation.

### Deferred to Follow-Up Work (from U10)

- **Astro scaffold for `/writing`**: `WritingLayout.astro`, `src/pages/writing/index.astro`, `src/pages/writing/[slug].astro`, `src/content/config.ts`. Built alongside the first real post, not in v1.
- **Sitemap + robots.txt exclusion** for `/writing`: moot until the route exists. Applies when the Astro scaffold lands.

---

- [ ] U11. **Lint + WCAG pass + Claude Design ingestion test + ship**

**Goal:** Validate the end-to-end work, run the R13a rubric against a live Claude Design ingestion (per brainstorm's pre-public-use gate), and ship the refreshed cbkdi.com.

**Requirements:** R2 (lint + WCAG AA), R13a (rubric-pass before public demo), R10 (ship together).

**Dependencies:** U2 (tokens), U3 (DESIGN.md), U4 (vendored), U5 (migrated), U6 (faces), U7 (wordmark), U8 (chrome + states), U9 (copy), U10 (/writing scaffold).

**Files:**
- Modify: `cbkdi/design-system/.github/workflows/lint.yml` — finalize (should already be green by now)
- Modify: `05 - Marketing/Website/cbkdi-website/docs/design-audit.md` — add a top-matter note: "Authoritative source of truth moved to `cbkdi/design-system`. This file is preserved as historical context for the pre-2026-04-23 site."
- Deploy: `05 - Marketing/Website/cbkdi-website/` via existing `npm run deploy` path (Astro build + Wrangler deploy to cbkdi.com).

**Approach:**
- **Design.md lint:** `npx @google/design.md lint DESIGN.md` locally; confirm zero errors. CI stays green.
- **WCAG AA contrast audit:** use `@google/design.md` CLI's contrast check OR manual Stark / color-contrast-checker against the full token matrix. Fix any failing pair (most likely candidate: purple on warm-dark at small sizes).
- **Claude Design ingestion test (per brainstorm pre-public-use gate):**
  - **Test against the real `cbkdi/design-system` repo**, not a throwaway. (Throwaway test for bare fetch-and-parse capability can happen once at U1 clone time if needed.)
  - Hand the real repo URL + intake blurb to `claude.ai/design`.
  - Run three seed prompts: "a landing page for a consulting practice," "a long-form writing post layout," "a proposal cover page."
  - Apply R13a rubric to each output. Pass = 2 of 3 meet the rubric. **Clarification of the 2-of-3 threshold:** 3 of 3 is an unreasonable bar given LLM output variance; 1 of 3 is insufficient signal. 2 of 3 means the system is reproducible enough to claim on a client call. Adjust if evidence from actual tests shifts the calibration.
  - If the real DESIGN.md does not pass, iterate on DESIGN.md body/YAML until it does. **Do not publicize the integration publicly** (client demos, marketing claims, proposal decks citing "this brand was generated via Claude Design") **until this passes.** Shipping the cbkdi.com refresh itself is **not** gated on this — only external claims about the Claude Design integration.
- **Full-site smoke test:**
  - Local build succeeds.
  - Playwright / manual sweep across Hero, About, The Work, Engagement, Contact, Footer in both modes; screenshot diffs against pre-refresh baseline.
  - /writing renders, TOC pattern works, reduced-motion honored.
  - Umami analytics still fires; CSP has no new violations in browser console.
  - A+ securityheaders.com check still passes.
- **Ship:**
  - Final copy review (one last pass on Hero/About/Work for tone).
  - `npm run deploy` from `05 - Marketing/Website/cbkdi-website/`.
  - Post-deploy: verify cbkdi.com live with new tokens, new chrome, new copy.

**Execution note:** Do **not** skip the Claude Design ingestion test in favor of shipping. The rubric gate is the whole point of R13a.

**Patterns to follow:**
- Existing `npm run deploy` workflow from `cbkdi-website/package.json`.
- Codex + `/ce-review` compound review pair per prior learning — run both on the final diff before shipping.

**Test scenarios:**
- *Happy path:* `npx @google/design.md lint DESIGN.md` returns zero errors.
- *Happy path:* All documented color pairs pass WCAG AA contrast in both modes.
- *Verification path (R13a):* Claude Design ingestion test passes (2 of 3 outputs meet the rubric).
- *Integration:* Post-deploy, cbkdi.com Lighthouse report is ≥ 95 on all four metrics (Performance, Accessibility, Best Practices, SEO).
- *Integration:* A+ on securityheaders.com preserved after deploy.
- *Edge case:* Contact form still submits successfully (no regression from token migration + middleware changes).
- *Error path:* If Claude Design ingestion fails the rubric, ship is blocked; iterate DESIGN.md.

**Verification:**
- DESIGN.md v1 is tagged `v0.1` (or `v1.0.0` — decide at tag time) in `cbkdi/design-system`.
- cbkdi.com shows the refreshed visuals + aligned copy at production.
- R13a rubric has been applied at least once to a live Claude Design output and passed.
- The pre-public-use gate from the brainstorm's Dependencies section is cleared.

---

## System-Wide Impact

- **Interaction graph:** The token migration touches every rendered page on cbkdi.com. The chrome-component introduction (U8) creates new interactive elements whose state behavior must play well with the existing `ThemeToggle` and with future interactive islands (e.g., the planned AI chat widget per `cbkdi-website/docs/ROADMAP.md` Phase 2). No middleware changes, but any new external font or image origin must be added to `src/middleware.ts` CSP — plan adds Google Fonts hosts (already allowed) or self-hosted font paths (same-origin, no CSP change needed).
- **Error propagation:** Token fallback failures (e.g., font-load failure) degrade to in-stack fallbacks. Contact-form failures remain handled in `src/pages/api/contact.ts`. Middleware continues to run on every response, including new `/writing` route.
- **State lifecycle risks:** Dark-mode toggle state persists in `localStorage` as today — unchanged. No new session or persistent state introduced. Any content-collection state for `/writing` is build-time, not runtime.
- **API surface parity:** Internal API unchanged. DESIGN.md's YAML front-matter is a new "API surface" for Claude Design and future agents; versioning discipline per the `cbkdi/design-system` repo's `v1.0.0` semantic tagging.
- **Integration coverage:** Cross-layer scenarios — dark-mode toggle + chrome-interaction-states + prefers-reduced-motion — require manual or Playwright verification; unit tests alone will not prove them.
- **Unchanged invariants:** `output: 'server'` preserved. Middleware CSP + nonce-injection preserved. Umami analytics path preserved. Contact-form API preserved. The Svelte 5 rune-based `ThemeToggle` is not modified. No new dependencies added to `package.json` except potentially font resources.

---

## Risks & Dependencies

| Risk | Mitigation |
|------|------------|
| Display serif choice lands "premium-restraint" again (Newsreader-attempt repeat) | U6 iterates with R13a rubric + real copy; side-by-side with pre-refresh state; explicit anti-regression check that output does not resemble Stripe Press / generic premium consulting. |
| Berkeley Mono licensing cost blocks the "distinctive" mono choice | U6 candidate list includes free alternatives as fallback; if the free options read as dev-docs, negotiate with brand priority — acceptable to pay if the mono is load-bearing for the systems signal. |
| Claude Design's ingestion behavior differs from what the intake screenshot suggests (private-repo handling, YAML parsing quirks, file-size limits) | U11 tests on a throwaway repo first; iterate on DESIGN.md if the rubric fails; do not publicize the integration until it passes. |
| Copy-sharpening positioning sentence doesn't land with all three exemplar audiences | U9 iterates 2–3 candidates + audience-resonance gut check; fallback is to keep "Senior judgment. Durable systems." and sharpen everything else. |
| Token migration breaks a section component visually | U5 executes with characterization screenshots before/after; intentional deltas are called out during U2's token authoring, not discovered during U5. |
| CSP regression from font or asset changes | Any new CDN origin requires middleware edit; `fonts.googleapis.com` already allowed. Verify A+ securityheaders.com after deploy. |
| Dropbox EPERM on new repo's first `npm install` | `com.dropbox.ignored` ADS set on build/cache dirs before first install (documented in U1). |
| Design-system repo drifts from cbkdi-website after initial vendoring | Manual copy-with-hash process is documented in U4; refresh cadence is opportunistic. Accept that drift happens; parity is not load-bearing unless brand-affecting. |
| `/writing` scaffold becomes a polished-empty orphan that never fills | R11 explicitly holds the live-nav link until the first post; no public surface exists yet. Publishing cadence is a separate effort (brainstorm-scheduled as follow-up). |
| Wrangler CLI nag prompts a version bump that breaks the Astro adapter | Pin wrangler version in `package.json`; don't bump on CLI nag without checking adapter compatibility. |

---

## Documentation / Operational Notes

- **Monitoring:** Umami at `https://analytics.cbkdi.com` continues to track page views. No new events needed unless publishing cadence emerges.
- **Rollout:** Single deploy to cbkdi.com via existing `npm run deploy` path. No feature flags, no phased rollout — the ship unit is the whole refresh. Rollback via `wrangler rollback` or redeploy prior main branch.
- **Docs to update:**
  - `05 - Marketing/Website/cbkdi-website/CLAUDE.md` — add "Design system vendoring" section (U4).
  - `05 - Marketing/Website/cbkdi-website/docs/design-audit.md` — mark historical; point to `cbkdi/design-system`.
  - `05 - Marketing/Website/cbkdi-website/docs/ROADMAP.md` — update Phase 2 to reflect that copy extraction is still deferred (explicitly not in this refresh).
  - `.claude/memory/project_website_status.md` — post-deploy, update with new ship date and link to `cbkdi/design-system`.
  - `cbkdi/design-system/README.md` — explains what it is, how Claude Design consumes it, adoption path for other CBKDI surfaces.
- **Post-ship follow-ups:**
  - Schedule the copy-extraction to `src/data/` as a separate bounded plan.
  - Schedule publishing-cadence brainstorm (first `/writing` post target date + live-route flip).
  - Consider whether Hilltop adopts the new tokens at its next refresh cycle.

---

## Sources & References

- **Origin document:** `05 - Marketing/design-system/docs/brainstorms/2026-04-23-cbkdi-design-system-requirements.md`
- **Related brainstorm:** `05 - Marketing/Website/cbkdi-website/docs/brainstorms/2026-03-23-messaging-evolution-requirements.md` (messaging broadening that precedes this plan's copy pass)
- **Related plan:** `05 - Marketing/Website/cbkdi-website/docs/plans/2026-03-23-001-feat-broaden-service-messaging-plan.md` (its copy changes are the starting point for U9's follow-on pass)
- **Current token reference:** `05 - Marketing/Website/cbkdi-website/docs/design-audit.md`
- **Project memory:**
  - `.claude/memory/project_cbkdi_positioning.md` (authoritative on positioning)
  - `.claude/memory/project_website_status.md` (prior Newsreader-attempt context)
  - `.claude/memory/user_cbkdi_brand.md` (brand-name conventions)
  - `.claude/memory/feedback_website_copy.md` (broaden-through-general-language rule)
  - `.claude/memory/reference_github_accounts.md` (cbkdi vs. thebanmagi GitHub scoping)
- **External:**
  - `github.com/google-labs-code/design.md` — template origin
  - `02ui.com` — primary visual reference (translated away from pixel-art; enumerated moves captured in DESIGN.md per R5a)
  - `inkandswitch.com`, `linear.app` — secondary visual references
