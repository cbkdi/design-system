# Claude Design intake — Phase 2 (cbkdi.com refresh)

Copy the two fields below into `claude.ai/design` when starting the Phase 2 session. Phase 1 (design-system finalization) landed as of this repo's main HEAD; Phase 2 applies it to cbkdi.com. The target repo is `cbkdi/cbkdi-website`, not this one.

## Form fields

- **GitHub repo**: `https://github.com/cbkdi/cbkdi-website` (the site being refreshed — Claude Design needs to see its current code)
- If the form accepts a second repo: `https://github.com/cbkdi/design-system` (the brand spec — `DESIGN.md` is authoritative). Otherwise reference it in the notes, which the draft below does.
- Skip `.fig` and `fonts/logos/assets` — none exist. The repos are the whole context.

---

## Field 1 — Company name and blurb

```
CBKDI (CBK Development Intelligence) — a one-person consulting practice working on systems, process, and product design for operators, viewed through a sponsor-side real-estate-development lens. Visual language: editorial voice inside opinionated structural chrome — warm dark near-black, single purple accent, three-face typography (Instrument Serif / Inter / IBM Plex Mono, Source Serif 4 for long-form), first-person copy, restrained flourish. Brand system finalized at github.com/cbkdi/design-system.
```

---

## Field 2 — Any other notes?

```
Phase 2 of a two-phase engagement. Phase 1 finalized the design system at
github.com/cbkdi/design-system — read DESIGN.md there first, it is the
authoritative brand spec. Do not re-decide faces, wordmark treatment, colors,
or /writing vocabulary; those are committed. Your job is to apply them to
cbkdi.com.

Target repo for changes: github.com/cbkdi/cbkdi-website
Stack: Astro 5 + Svelte 5 islands + Tailwind v4 + Cloudflare Workers.

The current site lives on a v0.1 of the brand. tokens.css is already vendored
at the finalized SHA (d6407e2) and section components already use named
tokens (text-hero, text-neutral-*, border-rule-*, etc.) so most of the token
migration is already done. What remains is the visible refresh: wordmark
markup, new chrome, interaction states, copy pass, content extraction.

Four units to close (numbered from the implementation plan at
cbkdi/design-system/docs/plans/2026-04-23-001-feat-cbkdi-design-system-plan.md):

1. U7 vendor-side — Wordmark markup in Header.astro

   Today the wordmark renders "• CBKDI" in Inter Semibold at 0.08em tracking.
   DESIGN.md commits Plex Mono Medium at 0.14em tracking, 0.8125rem
   (13px) in the header. Update src/components/layout/Header.astro's
   wordmark markup accordingly. The leading purple dot stays.

2. U8 — RevisionStamp + interaction states

   - Create src/components/ui/RevisionStamp.astro. Mono caption in
     var(--font-mono), 0.6875rem, color var(--color-text-lt) /
     dark:var(--color-text-lt-dark), 0.08em tracking, uppercase. Format
     "REV YYYY.MM" or "Updated YYYY-MM-DD". Source: front-matter lastmod
     if present, else git commit date of the page file. Insert in
     BaseLayout.astro or PageLayout.astro so every page carries it.

   - Token-drive ThemeToggle hover states. Current hardcoded
     hover:bg-[#f2f1f4] dark:hover:bg-[#2a2a2a] in
     ThemeToggle.svelte becomes hover:bg-neutral-100
     dark:hover:bg-neutral-800.

   - Contact form field states (src/components/sections/Contact.astro):
     default, focus (purple accent ring via var(--color-focus-ring)),
     error (var(--color-error-light) / var(--color-error-dark) + inline
     message, NOT browser-default red), disabled (opacity 0.5,
     aria-disabled="true", tabindex="-1"). Submit button: default,
     hover, focus-visible, loading (disabled + text swap), success
     (inline confirmation), error (inline message in error color).

   - 404.astro: remaining text-[#hex] and text-[clamp(...)] arbitrary
     values migrated to named tokens, aligning with the rest of the site.

   - Reduced motion: any new chrome animation wrapped in
     @media (prefers-reduced-motion: no-preference).

3. U9 — Copy pass + content extraction to src/data/

   Two things in one pass because both touch every section.

   Copy pass: the site currently leads with "Senior judgment. Durable
   systems." and a subhead that works. The positioning shift captured
   in 2026-04-23 calls for system / process / product design through a
   sponsor-side RE-development lens to be the headline, with fractional
   development-lead secondary. Draft 3-5 candidate single-sentence
   positioning lines. Lead with the verb-noun of what actually gets
   done, not with a branded noun-phrase. Test each candidate against
   three exemplar audiences:

     - a Steve-type sponsor (deal underwriting): does he see his
       problem?
     - an Erich-type first-time platform builder: does he see his
       problem?
     - a Greg-Kreider-type construction-company owner (systems /
       process work): does he see his problem? This last one is the
       hardest test and the best falsification — construction owners
       will not respond to "development intelligence for operators"
       because that reads as real-estate-developer-speak.

   Must pass all three. No em dashes anywhere in client-facing copy —
   hyphens only. First person throughout ("I", not "CBKDI" in third
   person). Do not use "Fractional Development Lead" as the headline.
   Do not enumerate the three audiences as separate service lanes —
   they are exemplars of one problem, not three products.

   Hero, About, The Work, Engagement, Contact copy all get updated to
   the new positioning. Existing copy is in src/components/sections/
   *.astro inline or in local const arrays.

   Content extraction: during the same pass, extract copy out of
   section components into typed TypeScript modules under src/data/:

     - src/data/site.ts       — nav items, footer links, brand name
                                variants (CBKDI / CBK Development
                                Intelligence), contact address.
     - src/data/hero.ts       — headline, subhead, CTA text.
     - src/data/about.ts      — bio paragraphs, credentials, meta grid.
     - src/data/work.ts       — heading, description, capabilities list.
     - src/data/engagement.ts — step titles + descriptions, heading.
     - src/data/contact.ts    — heading, email, brief grid fields.
     - src/data/testimonials.ts — if in v1 (confirm).

   Section components import from these modules; no inline copy
   after the pass. This also lands the Phase 2 prereq flagged in
   cbkdi-website/CLAUDE.md ("Content single source of truth").

   Finally, update the Claude Design intake blurb in
   cbkdi/design-system/DESIGN.md Overview > Claude Design intake blurb
   so the first line mirrors the committed Hero positioning sentence.

4. U11 — Lint, WCAG, ingestion test, ship

   - Contrast audit: run through every token pair actually used on the
     rendered site at WCAG AA in both modes. Flag any near-misses.
   - Full-site smoke: Hero, About, The Work, Engagement, Contact,
     Footer, 404 in both modes. /writing stays as DESIGN.md spec
     only — no live route yet, that ships with the first real post.
   - Post-deploy: Lighthouse should stay ≥95 on all four metrics;
     securityheaders.com should stay A+. Umami analytics must continue
     firing. CSP should show no new violations in browser console.
   - Claude Design ingestion test (per the R13a rubric in DESIGN.md):
     once the refresh is live, the separate ingestion pass at
     claude.ai/design (pointed at cbkdi/design-system) should
     produce output that passes the rubric — 2 of 3 on a landing /
     writing-post / proposal-cover seed-prompt round. This gates
     external claims about the integration, not the cbkdi.com ship
     itself.

Constraints (will not bend):

- Voice: first-person, hyphens not em dashes, no "Fractional" headline,
  no third-person "CBKDI does X" in body copy. These are the site-wide
  rules in DESIGN.md Do's and Don'ts.
- Identity: typographic only. No pictorial logos, no stock photography,
  no figurative illustration.
- Palette: single-accent purple, editorial-flat. No shadows, no blur,
  no second accent hue.
- Build invariants: output: 'server' stays (middleware must run); do
  NOT enable experimental.csp; do NOT create public/_headers; do NOT
  re-add mode-watcher (the hand-rolled ThemeToggle.svelte is
  intentional). Section components MUST keep their id attributes
  (id="about", id="services", id="engagement", id="contact") for
  anchor navigation.
- No new npm dependencies unless explicitly justified. The existing
  middleware (src/middleware.ts) handles security headers + CSP nonces
  and must not be modified.
- No changes to hilltop.cbkdi.com (lives in a separate repo,
  cbkdi/hayden-hilltop) or to Kreider handouts, proposal generator,
  or email signatures. Those adopt the refreshed brand opportunistically
  later.

Out of scope for this pass:

- /writing Astro scaffold (WritingLayout.astro, pages/writing/, content
  collection). That ships alongside the first real post. DESIGN.md
  already specifies the vocabulary.
- First /writing post content itself.
- Publishing cadence decisions.
- Case-study publishing.

Deliverables:

- Proposed edits to cbkdi-website files, either as PR-ready diffs or
  as clearly labelled file contents I can apply as PRs. Prefer
  concrete code + copy over design mockups — the design system is
  already settled, so the work here is implementation.
- Final committed positioning sentence + the three-audience
  resonance-test reasoning that justified the choice.
- RevisionStamp component implementation (Astro component + the
  BaseLayout or PageLayout insertion).
- src/data/*.ts typed modules with the refreshed copy.
- Interaction-state implementations or specs for the Contact form
  and ThemeToggle.
- R13a rubric walkthrough against the rendered refresh, in both
  modes, on a representative screen (Hero on laptop + mobile is the
  minimum).

Reference files to read before starting:

- github.com/cbkdi/design-system/DESIGN.md  — brand spec
- github.com/cbkdi/design-system/tokens.css — tokens
- github.com/cbkdi/design-system/docs/plans/2026-04-23-001-feat-cbkdi-design-system-plan.md — units U7/U8/U9/U11
- github.com/cbkdi/cbkdi-website/CLAUDE.md — site constraints, middleware, CSP, Phase 2 prereq
- github.com/cbkdi/cbkdi-website/docs/design-audit.md — current copy + token reference (historical, not authoritative)
- github.com/cbkdi/cbkdi-website/src/styles/tokens.css — vendored tokens at d6407e2
- github.com/cbkdi/cbkdi-website/src/components/sections/*.astro — current section code
- github.com/cbkdi/cbkdi-website/src/layouts/BaseLayout.astro — font loading already set for the four faces
- github.com/cbkdi/design-system/docs/comps/2026-04-24-faces/ — Phase 1 comps + rubric walkthrough, useful as a positive reference

When you want to see the finalized system in motion before committing
Phase 2 edits, docs/comps/2026-04-24-faces/Comps.html in the
design-system repo renders Hero / About / /writing in both modes.
```

---

## After Phase 2 lands

- Run `scripts/refresh-tokens.sh` in cbkdi-website if the design-system's `tokens.css` moved during Phase 2. Usually it won't — Phase 2 is consumer-side.
- Claude Design's output should come back as file contents / diffs. Apply as PRs through the usual flow (branch + PR + merge).
- Final R13a ingestion test runs against the refreshed cbkdi.com + the finalized DESIGN.md, per U11. Pass = 2 of 3 on the three seed prompts (landing / writing-post / proposal-cover). Failure doesn't block the ship — it only blocks external claims about the Claude Design integration.

## Phase 3 (not scheduled)

Once Phase 2 is live, the remaining follow-ups in the plan's "Deferred to Follow-Up Work" section can move at their own cadence:
- First `/writing` post + live route flip.
- Non-website surface adoption (Hilltop, proposal generator PDF regen, email signatures, Kreider handouts).
- Publishing-cadence brainstorm.
- Any paid-face upgrade or additional display weight if needs emerge.
