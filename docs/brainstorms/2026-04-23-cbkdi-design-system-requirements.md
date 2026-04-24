---
date: 2026-04-23
topic: cbkdi-design-system
---

# CBKDI Design System and Website Refresh

## Problem Frame

CBKDI's current website was built to sell one service lane — deal underwriting / "Fractional Development Lead" for real estate sponsors. Six months in, the work that has actually landed, and that Conor wants to continue doing, is **systems and process / product-design consulting viewed through a sponsor-side real-estate-development lens** — turning ambiguous, multi-party operator problems into durable systems. Fractional development-leadership hourly work remains available for the right deal, but it is explicitly **not** the headline anymore.

The 2026-03-23 messaging pivot ("Senior judgment. Durable systems.") moved in this direction by broadening from one service lane to three audiences. This brainstorm carries the positioning one step further: the center of gravity is not three parallel lanes, it is **one frame** (systems / process / product design) with **RE-development discipline as the distinctive claim**. The three audiences (RE sponsor, first-time platform-builder, construction company owner) are exemplars of the kind of problem, not parallel service offerings.

The visual identity has not caught up to either the 03-23 pivot or this further refinement. Separately, the Claude Design tool (claude.ai/design) has launched, and it consumes a `DESIGN.md` artifact — Google-Labs has shipped an open spec and CLI for exactly this format. CBKDI needs a real, machine-readable brand system that (a) refreshes cbkdi.com to match the current positioning, (b) governs future surfaces as they refresh, and (c) feeds Claude Design so it can generate CBKDI-branded UIs on demand.

The design system is also thematically load-bearing: the practice sells "durable systems," and maintaining a public, lint-checked design system is credible evidence of the thing being sold.

> **Non-premise.** A design system is a brand-quality lever, not a demand-gen lever. It raises the ceiling on every future touchpoint; it does not by itself generate inbound. The high-leverage marketing moves — published thinking, case studies, distribution — are separate efforts and sit outside this brainstorm's scope.

---

## Actors

- A1. **Conor Keilty** — Principal. Brand owner; decision authority on voice, visual direction, logo, and publishing cadence.
- A2. **Claude Design (claude.ai/design)** — Primary programmatic consumer. Reads the public GitHub URL, applies the design system to generate CBKDI-branded UI on request.
- A3. **Future contributors / contractors** — Occasional human contributors (designers, developers) who consume the DESIGN.md to stay on-brand. Includes any future LLM coding agents working in CBKDI repos.
- A4. **Prospective clients** — Visual targets for the refresh; do not read the design system directly but consume its output via cbkdi.com and the Writing section. Operators whose problem benefits from systems / process / product-design thinking applied through a sponsor-side-RE-development lens. Exemplar types per the 03-23 messaging doc: RE sponsor (Steve-type), first-time platform-builder (Erich-type), construction company owner (Kreider-type). **These are exemplars of the kind of problem, not three parallel service lanes.**

---

## Key Flows

- F1. **Hand CBKDI to Claude Design**
  - **Trigger:** Conor opens claude.ai/design and pastes the CBKDI blurb + `https://github.com/cbkdi/design-system` URL.
  - **Actors:** A1, A2
  - **Steps:** Claude Design fetches the repo → reads `DESIGN.md` front-matter tokens and body → asks clarifying questions if needed → generates a CBKDI-branded UI for whatever prompt Conor gives it.
  - **Outcome:** Generated UI looks unmistakably CBKDI: three-face type system, mono structural chrome, monochrome + purple on warm dark, restrained editorial voice. No re-training, no pasting tokens, no custom prompts beyond the intake blurb.
  - **Covered by:** R1, R2, R3, R13

- F2. **Refresh cbkdi.com using the design system**
  - **Trigger:** DESIGN.md v1 is tagged; cbkdi-website is ready for a styling pass.
  - **Actors:** A1, A3
  - **Steps:** Import the design-system tokens into `05 - Marketing/Website/cbkdi-website/src/styles/global.css` → apply the refreshed typography and structural chrome to existing single-page sections → add the `/writing` content surface → ship the 2026-03-23 copy on top of the new visuals.
  - **Outcome:** cbkdi.com is visibly refreshed, the three audience types see themselves reflected, and the new chrome (mono labels, breadcrumbs, revision stamps, dark-card containers) is legible as part of the brand. The `/writing` route is *specified* in DESIGN.md and ready to ship with the first real post — not built as an empty surface.
  - **Covered by:** R5, R6, R7, R8, R10, R11, R12

- F3. **Future surface adopts the system (opportunistic)**
  - **Trigger:** Any CBKDI-branded surface (Hilltop, proposals, emails, Kreider handouts) enters a refresh cycle.
  - **Actors:** A1, A3
  - **Steps:** Surface owner reads the current DESIGN.md → imports tokens or reads rationale → applies to the surface being refreshed → opens a PR against `cbkdi/design-system` if the surface exposes a gap the system should cover.
  - **Outcome:** Coherence accrues without a big-bang migration. v1 does not require all surfaces to refresh at once.
  - **Covered by:** R4, R14

---

## Requirements

**Design system repo**

- R1. The design system lives at `github.com/cbkdi/design-system`, **public**, forked from `google-labs-code/design.md`, Apache 2.0.
- R2. The repo conforms to Google's `design.md` spec: YAML front-matter tokens + markdown body with canonical sections (Overview, Colors, Typography, Layout, Elevation & Depth, Shapes, Components, Do's and Don'ts). Passes `@google/design.md` lint cleanly, including WCAG AA contrast rules for both modes.
- R3. The root `DESIGN.md` is self-contained and portable — readable as a single file if pasted into a tool that does not fetch the GitHub URL. No critical content is hidden in child files the spec does not surface.
- R4. The repo ships a short top-level `README.md` explaining what it is, how Claude Design consumes it, and how other CBKDI surfaces adopt it. Upstream sync with `google-labs-code/design.md` is a light-touch practice, not an automated obligation.

**Visual direction**

- R5. The visual language is **editorial voice inside opinionated structural chrome** — closer to 02ui.com (translated away from its pixel-art costume) than to the premium-restraint school (Mod / Brown / Pawson / Stripe Press). Reading quality is preserved; generic-consulting polish is rejected. Primary references: 02ui.com (structural chrome, three-face system, hot-accent-on-warm-dark), Ink & Switch (editorial craft for a small practice), Linear (typographic precision bar).
- R6. Dark mode is native and **warm** — slightly warm near-black, not pure cool `#000`. Both modes are fully specified. Purple (`#4f3d78` light / `#a78bdb` dark, from `docs/design-audit.md`) is the single hot accent on an otherwise monochrome field; no secondary brand colors. Exact warm-black value is a planning-level call.
- R7. **Three-face type system** with explicit jobs for each face:
  - **Display serif** — hero, section heads, post titles, long-form article titles. A face with character, not a generic premium serif. "Attitude vs. discipline" is resolved through planning/iteration (comps on real copy), not in this brainstorm.
  - **Body** — Inter for landing and UI (preserves the current site's foundation). A reading serif (candidates to evaluate: Source Serif 4, Tiempos Text) is under consideration specifically for `/writing` long-form pages; decision deferred to planning.
  - **Monospace** — all structural chrome: nav, breadcrumbs, labels, metadata, captions, revision/date stamps, tabular data, footnote numerals, section anchors. Uppercase + tracked for labels by default. Candidates to evaluate: Berkeley Mono (paid, distinctive), JetBrains Mono, Geist Mono, IBM Plex Mono.
  - Fluid sizing via `clamp()` is preserved from the current implementation.
- R8. **Structural chrome does work, not decoration.** The mono-driven chrome is the primary mechanism for signaling "systems" inside the editorial frame. Required elements: breadcrumbs on non-landing pages; a table-of-contents on long-form `/writing` posts; revision/date stamps in mono at the foot of every page; soft-cornered dark-card containers for structural content (TOC, callouts, data blocks); section anchors (§01-style) used sparingly, never as the whole-brand signature. Chrome appears only where it earns its place; pages without structural content stay quiet.
- R5a. **Reference anchor is captured, not pointed at.** DESIGN.md includes an enumerated list of the **specific moves being borrowed from 02ui.com** (translated away from its pixel-art costume) — e.g., three-face type system with mono structural chrome, hot-accent-on-warm-dark palette, soft-cornered dark-card containers, uppercase-tracked-mono labels, explicit breadcrumb / TOC / revision-stamp chrome, specific type-contrast register. This captured list is the durable reference, not the live site URL. Prevents "reference drift" (Conor's read of 02ui.com changes, or the site itself changes) from re-opening settled direction calls at planning or first-comp review.
- R8a. **Interaction states are specified for every chrome element, not left to implementer discretion.** Every chrome element (nav link, breadcrumb link, TOC item, card container, §-anchor, inline link) specifies default, hover, focus-visible, active / current-section, and disabled states in both modes. The active-TOC-item state uses a **non-color** differentiator (weight change, left-border indicator, or underline) to preserve the strict single-accent purple convention — a second accent value is not introduced for active-state. Focus-visible retains the current site's accent-ring treatment, carried forward into the mono chrome. Reduced-motion (`prefers-reduced-motion: reduce`) disables all chrome transitions, mirroring the existing site's accessibility posture.

**Identity**

- R9. The CBKDI identity stays **typographic** — a refined wordmark, not a pictorial mark. The exact treatment of the purple dot in the current `• CBKDI` mark is decided during planning; a pictorial icon is explicitly out of scope.

**Website refresh (cbkdi.com)**

- R10. The homepage refresh is a **re-skin** — same section order (Hero, About, The Work, Judgment/Room, Engagement, Contact), new visuals. **Ship unit: visuals + copy together, not visuals with stale copy.** The 2026-03-23 messaging copy receives a follow-on pass (Hero, About, The Work, and intake-blurb mirror) to align with the 04-23 positioning refinement — systems / process / product design as the headline with sponsor-side-RE-development discipline as the differentiator, fractional dev-lead explicitly demoted — **before** the re-skin ships. No phased/partial ship where the new visuals carry pre-refresh copy; that would create a split-personality window in which Success Criterion #2 fails by construction. No restructure of the single-page anchor flow.
- R11. A new `/writing` (or `/notes`) surface is planned for cbkdi.com. **DESIGN.md v1 fully specifies** the writing-layout vocabulary (reading body face, long-form type scale, TOC pattern per R8 and the responsive decision deferred below, breadcrumb, revision stamp, footnote treatment) so planning has a complete token set. **The live cbkdi.com/writing route ships with the first real post, not empty.** This removes the polished-empty-surface displacement risk and keeps v1 focused on the homepage refresh + design-system artifact. Revised 2026-04-23 post doc-review on scope-guardian finding.
- R12. The refresh is shipped via `05 - Marketing/Website/cbkdi-website/`, importing tokens from the design-system repo. No duplicate token definitions between the two repos.

**Agent and tool compatibility**

- R13. A short "Claude Design intake blurb" is maintained in the design-system repo for paste-ready use in claude.ai/design. Draft in Key Decisions below; refine at planning time.
- R13a. **"Visibly, unmistakably CBKDI" has a concrete rubric.** Success Criterion #1 is falsifiable against this rubric, not a subjective read.
  - **Must-haves (all pass)**: three-face system visible in the output (a serif for display / headings, Inter or acceptable sans for body, and monospace somewhere in the chrome); warm dark field (not cool `#000`); purple as the only saturated accent; first-person voice in any generated copy; monospace appears in at least one chrome element (nav, breadcrumb, label, caption, revision stamp, or tabular header).
  - **Should-haves (3 of 5 pass)**: section anchors (§01-style) or equivalent structural-anchor treatment; soft-cornered container cards for structural content; uppercase + tracked treatment on labels; breadcrumb or TOC chrome on any non-landing page; revision / date stamp in mono somewhere visible.
  - **Must-not-haves (any violation = fail)**: pictorial icon treated as the brand mark (wordmark only); generic consulting stock photography; non-purple warm / saturated accent (blue-green, orange, red); carousel / testimonial-slider chrome; pure cool `#000` dark background.
  - **Overall pass**: all must-haves + 3 of 5 should-haves + zero must-not-have violations.
- R14. **Tokens flow CSS-first.** `cbkdi/design-system` authors the Tailwind v4 `@theme` block directly as a single static CSS file (e.g., `tokens.css`) that serves as the authoritative token source. The design.md YAML front-matter mirrors these values so the `@google/design.md` lint still runs and Claude Design reads a schema-conforming file. cbkdi-website imports the CSS directly (via `@import "https://raw.githubusercontent.com/cbkdi/design-system/main/tokens.css"` at build time or an equivalent local-copy mechanism — planning resolves the exact distribution). **No transform step, no build-emitted output, no parallel token set.** Dark mode is expressed in the same CSS via a `[data-theme="dark"]` selector or the existing `html.dark` class the site already uses. Decision made 2026-04-23 post-review.

---

## Success Criteria

- Claude Design, fed only the blurb and the repo URL, produces a UI that is visibly, unmistakably CBKDI — without additional prompting about colors, type, or voice.
- The refreshed cbkdi.com reads as a polished evolution of the current site, not a new brand. A prospect who visited last week recognizes it. A prospect landing for the first time sees **systems / process / product design, applied through a sponsor-side RE-development lens**, as the primary offering — not "fractional development lead." The three exemplar audiences (sponsor, platform-builder, construction owner) each see their own problem reflected; none feels like the "target" lane.
- The `/writing` vocabulary is fully specified in DESIGN.md (reading body, TOC pattern, breadcrumb, revision stamp, footnote treatment) so the first post can be published as a one-shot build rather than a multi-decision scramble. The live route does not ship empty.
- A future CBKDI-branded surface (e.g., a proposal PDF, an email template, a new side-project page) can adopt the system by reading `DESIGN.md` alone — no synchronous ask of Conor required.
- `@google/design.md lint` passes on the repo. WCAG AA contrast holds in both modes.

---

## Scope Boundaries

- **Not a pictorial logo.** The identity stays typographic. No icon, no monogram glyph in v1.
- **Not a rebrand.** "CBKDI" / "CBK Development Intelligence" names, purple accent, Inter body, and restrained editorial voice are all preserved. The refresh sharpens, it does not replace.
- **Not a cbkdi.com restructure.** Single-page anchor flow stays; only `/writing` is added as a new surface in v1.
- **Not case-study publishing.** Sourcing, writing, or gating case studies is a separate effort. The design system accommodates them; v1 does not require any.
- **Not covering all CBKDI surfaces in v1.** Hilltop (`hilltop.cbkdi.com`, existing SvelteKit), the Node proposal generator in `04 - Templates/`, email signatures, and Kreider handouts adopt the system opportunistically as they're revised. v1 explicitly does not re-skin them.
- **Not writing essays.** Content production is not part of this brainstorm. The live `/writing` route ships with the first real post (see revised R11); it does not ship empty.
- **Not a demand-gen initiative.** This work raises brand quality; it does not substitute for the distribution/publishing moves that actually generate inbound.
- **No automated upstream fork sync.** Pulling from `google-labs-code/design.md` is a manual, occasional practice.

---

## Key Decisions

- **Systems / process / product design is the headline — not fractional development leadership.** The practice sells systems thinking applied through a sponsor-side real-estate-development lens. Fractional dev-leadership hourly work is available for the right ask but is explicitly secondary. This is a refinement on top of the 2026-03-23 "Senior judgment. Durable systems." pivot: that pivot broadened to three audiences; this brainstorm names one frame with RE-development discipline as the distinctive claim. The design system and the refreshed site must reflect this positioning; the site copy may also need a follow-on pass (see Outstanding Questions).
- **Durable brand system, not a Claude-Design feeder.** The repo is a first-class brand artifact that happens to be LLM-readable. It governs cbkdi.com today and every CBKDI-branded surface as each refreshes.
- **Public repo.** Under `cbkdi/` GitHub org. Claude Design can fetch directly; public maintenance reinforces the "durable systems" positioning.
- **Fork of `google-labs-code/design.md`.** Inherit the spec, lint, and canonical-section structure. Fork relationship is a credibility feature, not a liability. The upstream Tailwind-export CLI is **not** used — CBKDI is CSS-first (see next decision).
- **CSS-first token authoring (decided 2026-04-23 post-review).** The authoritative token source is a hand-authored Tailwind v4 `@theme` CSS block in `cbkdi/design-system` (see R14). The design.md YAML front-matter mirrors those values for lint + Claude Design ingestion, but CSS is the source of truth. Trade-off: gives up the upstream CLI's direct Tailwind export in exchange for zero transform cost, zero parallel-token convention, and native dark-mode via CSS selectors. Right call for a one-person practice.
- **Editorial voice inside opinionated structural chrome.** Three-face type system (display serif with character, Inter body, monospace chrome), single purple accent on a warm near-black field, soft-cornered dark-card containers for structural content. Primary reference: **02ui.com**, translated away from its pixel-art costume; secondary references: Ink & Switch (editorial craft for a small practice) and Linear (typographic precision bar). Rejected alternatives: premium-restraint school (Mod / Brown / Pawson / Stripe Press) as too generic for the "thinker + writer + producer" target; pure-architectural / blueprint chrome as too costumed; technical / dev-docs as positioning drift toward dev-tools; "no signature move" editorial as underpowered against the consulting-crowd bar.
- **Dark warm field, not cool.** Slightly warm near-black. Exact value TBD at planning. Current site's `#111` is slightly cool and is a candidate for replacement.
- **Mono carries the systems signal.** Inside the editorial frame, monospace is where "systems" shows up — labels, breadcrumbs, revision stamps, tabular data, footnote numerals. No need for architectural theming; the chrome does the work.
- **Refine the current wordmark; no pictorial mark.** The exact treatment (keep the purple dot, reposition, or retire) is decided in planning.
- **Website refresh: re-skin + add `/writing`.** The existing single-page structure holds; the Writing surface is the compounding lever the current site lacks, and it is also the natural home for the full structural-chrome vocabulary (TOC, breadcrumbs, footnotes, revision stamps).
- **Claude Design intake blurb (draft v1 — revised 2026-04-23 for positioning shift):**
  > **CBKDI (CBK Development Intelligence).** Systems, process, and product-design consulting viewed through a sponsor-side real-estate-development lens: I help operators turn ambiguous, multi-party problems into durable systems that hold up in the room. Drawing on 15 years across field construction, architecture, underwriting, entitlement, capital structuring, and sponsor-side execution. Fractional development leadership is available for the right deal but is not the headline. Website and long-form Writing section at cbkdi.com.
  >
  > **Brand:** editorial voice inside opinionated structural chrome. Three-face type system — display serif with character (hero / section heads), Inter for landing-page body and UI, and monospace for all structural chrome (nav, breadcrumbs, labels, metadata, captions, revision stamps, tabular data). Single purple accent (`#4f3d78` light / `#a78bdb` dark) on a warm near-black field. First-person voice. Dark mode native.

---

## Dependencies / Assumptions

- The `cbkdi` GitHub account (per `CLAUDE.md`) has permission to create public repos under the `cbkdi` org. To be verified during planning.
- Claude Design can fetch public GitHub URLs without special handling. Inferred from the intake screenshot; worth verifying on the first real hand-off.
- `google-labs-code/design.md` Apache-2.0 terms permit a CBKDI-branded fork. Verified from WebFetch summary of the repo; re-verify against `LICENSE` on fork.
- The cbkdi-website Astro + Svelte + Cloudflare Workers stack stays. Tokens flow from design-system → cbkdi-website/`src/styles/global.css` via a generated or derived mechanism.
- The 2026-03-23 messaging copy (`05 - Marketing/Website/cbkdi-website/docs/brainstorms/2026-03-23-messaging-evolution-requirements.md`) is the authoritative source for hero/about/work/engagement/contact text — but with the 2026-04-23 positioning refinement layered on top (systems / process / product design is the headline, not fractional dev-lead). A follow-on copy pass may be needed; tracked in Outstanding Questions.
- **Prior failed design attempt (context for planning):** Per `project_website_status.md`, a prior refresh tried Newsreader serif + increased spacing + scroll animations and was rejected by Conor. That attempt appears to have been a "premium-restraint" style refresh without the opinionated-chrome signal. This brainstorm deliberately moves in a different direction (editorial voice **inside** opinionated structural chrome, 02ui.com-derived) — planning should not silently regress to the earlier premium-restraint frame.
- **Pre-public-use gate (post-review, 2026-04-23):** DESIGN.md v1 cannot be publicized (e.g., linked in a client demo, handed to claude.ai/design in a live prospect conversation) until the R13a rubric has been applied to a live Claude Design test and passed. **Verification protocol:** create a throwaway public repo with a minimal DESIGN.md (one color pair + three font-family slots + the intake blurb from Key Decisions). Hand it to claude.ai/design with the blurb. Run three seed prompts — "landing page for a consulting practice," "a long-form writing post layout," "a proposal cover page." Apply R13a to each output. Pass = 2 of 3 meet the rubric. This is not a planning blocker (planning can proceed); it is a public-use blocker.

---

## Outstanding Questions

### Resolve Before Planning

*(none — all decisions that would block planning are made. Resolved 2026-04-23 post-review.)*

### Deferred to Planning

- [Affects Problem Frame, Key Decisions, intake blurb, R10 copy][User decision + Needs iteration] **Sharpen the positioning sentence.** The current phrasing — "systems, process, and product-design consulting viewed through a sponsor-side real-estate-development lens" — stacks three generic practice words in front of the actual differentiator, risking a "consultant broadening" read instead of sharpening. Planning must produce a **single-sentence positioning line** that leads with the RE-development-discipline differentiator and is tested for resonance against the three exemplar prospect types (Steve / Erich / Kreider). Example starting directions to iterate on (not final): "Development intelligence for operators — sponsor-side real-estate discipline applied to the systems, processes, and products your business runs on." Blurb (R13) must mirror the chosen line; site Hero and About copy may need a follow-on pass to align (cross-refs the separate 03-23-copy follow-on question below).
- [Affects R8, R11][User decision + Needs iteration] **Responsive TOC strategy on `/writing` posts.** Four patterns to evaluate on real comps: (a) sidebar at ≥ lg, collapsible dropdown drawer < lg with sticky toggle in mono; (b) inline top-of-post summary block (collapsible) at all viewports, no sidebar; (c) fixed sidebar that hides entirely < lg; (d) persistent drawer on mobile with scroll-spy. Decision drives markup architecture, ARIA pattern, and scroll-spy behavior for every long-form post, so it cannot be deferred past the first `/writing` comp. Accessibility requirements: keyboard-navigable (Tab through items, Enter to activate), active-section communicated via `aria-current`, focus-visible treatment carried forward.
- [Affects R10][User decision] **Does the 2026-03-23 messaging copy need a follow-on pass** to reflect the further positioning refinement (systems / process / product design with RE-lens as primary; fractional dev-lead as secondary, not a co-equal lane)? The 03-23 doc was written to broaden from deal-only to three parallel audiences; this brainstorm names the frame as one (systems / process / product) with three exemplars. Likely yes for the Hero, About, and The Work sections. Decide after the first visual comp lands, and route via `05 - Marketing/Website/cbkdi-website/docs/brainstorms/` rather than this design-system brainstorm.
- [Affects R7][Needs research + iteration] **Display serif — attitude vs. discipline.** "Attitude" candidates with character: GT Sectra, Fraunces (high-contrast axis), Migra, Beatrice Display, Editor's Note, Romie, Instrument Serif. "Disciplined" candidates: Source Serif 4, Tiempos Headline, Equity Caps, GT Super. Resolve through planning + real comps on CBKDI copy; the choice evolves rather than being decided up-front.
- [Affects R7][Needs research] **Monospace face.** Candidates: Berkeley Mono (paid, distinctive, worth the cost if the brand leans on it), JetBrains Mono, Geist Mono, IBM Plex Mono. Licensing and rendering at small sizes both matter.
- [Affects R7][User decision] **Body face on `/writing` pages.** Inter (keeps the site on one body face; faster to ship) vs. a reading serif (stronger long-form reading quality; introduces a second family). Decide after a real writing-layout comp.
- [Affects R6][Technical] **Warm-near-black value** for dark mode. Current site uses `#111` (slightly cool). Pick a deliberate warm value (e.g., `#0f0e12`, `#121014`) with measured contrast against purple `#a78bdb` and body text.
- [Affects R6][User decision] **Purple handling across modes.** Does purple stay strict single-accent, or is there a lighter-purple / accent-pair for specific uses (e.g., active TOC item vs. link hover)? Strict single-accent is the current convention.
- [Affects R6][User decision] **Default mode for first-paint.** Current behavior respects `prefers-color-scheme`. Given the "dark mode look" preference, planning should confirm whether dark is the authored-for mode (comps and primary design work happen in dark), the default for first paint, or both.
- [Affects R9][User decision] **Wordmark treatment for the purple dot.** Keep leading dot, move to center-height inline, retire entirely, or replace with a structural mark (em-rule, section sign, middle-dot). Decide alongside the display face in planning.
- [Affects R11][User decision] **Route name for the writing surface.** `/writing` vs. `/notes` vs. `/essays` vs. `/journal`. Soft decision; affects tone.
- [Affects R14][Technical] **Token flow mechanism** from design-system repo into cbkdi-website's Tailwind v4 `@theme` block: git submodule, npm package, generated CSS imported via `@import`, or copy-on-release. Lowest-friction option that also survives editing both sides.
- [Affects R1][Technical] **Fork vs. `Use this template`** on the Google repo. A fork preserves upstream-sync optionality; a template copy starts clean. Default is fork; re-confirm at clone time.
- [Affects R2][Technical] **Canonical-section content depth.** Which canonical sections from the `design.md` spec need CBKDI-specific content, inherited defaults, or deliberately-minimal treatment (e.g., "Elevation & Depth" is likely near-empty for this editorial-flat aesthetic).
- [Affects R12][Technical] Does the cbkdi-website `CLAUDE.md` need an update to reference the external design-system source of truth? Likely yes.

#### From 2026-04-23 agent review — bulk appended

*Design / visual (design-lens + adversarial + product-lens):*
- [Affects R7][Needs iteration] **Display-serif weights and italic coverage** — candidate faces have materially different axis coverage (Fraunces variable vs. GT Sectra Book/Medium/Bold/Black vs. Romie's narrower range). h1/h2/h3 hierarchy on `/writing` posts depends on this. Pin at face-selection time.
- [Affects R7][Technical] **Monospace fallback stack** — no fallback specified. Berkeley Mono load failure would degrade brand-critical chrome to Courier New. Pin at least one free fallback (JetBrains Mono / Geist Mono / IBM Plex Mono) in the stack's second position.
- [Affects R7][User decision + Product risk] **Three-face system is load-bearing but all three faces deferred** — if Berkeley Mono is rejected on cost/licensing, the free fallbacks risk reading as developer-docs drift (rejected in Key Decisions). Plan to evaluate the chrome signal with each candidate combination on real comps before committing, and name a face-swap escape hatch if needed.
- [Affects Problem Frame, R5, Key Decisions][Product risk] **"Mono carries the systems signal" is genre-coded** — for Steve/Kreider operators who are not fluent in the Linear / Ink-&-Switch aesthetic, mono may read as "under construction" or "code" rather than "systems." Test mono-chrome density on real comps against the named audience before committing to the mono-everywhere convention.
- [Affects R10, Success Criteria][Design] **Three-exemplar framing needs a structural mechanism on the page** — doc asserts the three audiences are exemplars not parallel lanes, but R10 preserves section order built for three-audience broadening. Add a unifying problem-statement block above The Work, or another connective-language mechanism, so the page reads as one practice not three. Partially addressed by the positioning-sharpening question above; site-structure-level work remains.

*Product / strategy (product-lens + adversarial):*
- [Affects Problem Frame, Key Decisions][Product risk] **Downgrade the "design system as credible evidence of durable systems" claim** — the three exemplar prospects are not plausible GitHub-repo readers. Brand-quality + Claude Design consumption are the real justifications; the thematic-evidence framing is rationalization that inflates repo maintenance pressure. Do not market the repo publicly as evidence; the Non-premise note already scopes this correctly.
- [Affects Problem Frame][Product] **Schedule the publishing-cadence brainstorm as a follow-on** before the design-system tag is used to claim durable-systems credibility. Design-system work is brand-quality, not demand-gen; inbound requires published thinking and distribution. `/writing`-route-deferral (applied) partly addresses this.
- [Affects F1, Success Criteria #1][Gate] **No external demo of the Claude Design integration** until the pass/fail rubric (captured in Resolve-Before-Planning above) has been applied once and passed. Prevents a generic-AI-output moment from inverting the credibility claim mid-conversation.

*Scope / language hygiene (scope-guardian + coherence):*
- [Affects Problem Frame, F3][Scope] **"Governs all future CBKDI-branded surfaces" overstates v1 reach** — language implies a migration mandate that the scope-boundary explicitly rejects as opportunistic. Soften "governs" at planning (e.g., "offers a reference point for" or "is opt-in adopted by").
- [Affects R1][Verification] **Confirm cbkdi-org public-repo creation permission** on the `cbkdi` GitHub account. Pre-condition for R1.
- [Affects R1, R2, R14][Verification] **Re-verify google-labs-code/design.md's Apache-2.0 terms and any patent-grant language on fork.** Re-confirmed against `LICENSE` at clone time, not inferred from repo summary.
- [Affects Dependencies / Assumptions][Concrete fix — gated_auto eligible] **Embed a Newsreader-attempt summary inline** in Dependencies rather than forward-referencing `project_website_status.md`. Keeps the anti-regression note self-contained when the memory file is not at hand.
- [Affects whole doc][Terminology] **Disambiguate "planning" throughout.** The word covers both pre-implementation design refinement (color / serif / wordmark iteration) and `/ce-plan` implementation planning. Pick and apply a consistent split (e.g., "design refinement" vs. "planning"). Safe-auto-eligible once the naming convention is picked.
- [Affects R6][Cross-reference] **Anchor `docs/design-audit.md` path at first mention** — resolves to `05 - Marketing/Website/cbkdi-website/docs/design-audit.md`. Currently forward-referenced without path context.

*Rolled up into applied requirements (no further action needed, noted for audit trail):*
- Reduced-motion behavior (design-lens P2) — folded into R8a.
- Empty-state design, breadcrumb truncation, TOC keyboard nav, breadcrumbs-with-no-consumer — all moot via R11 revision (live route ships with first post).
- Intake-blurb generic framing (product-lens P2) — will be addressed as part of the positioning-sharpening iteration above (R13 blurb mirrors the chosen positioning line).
- Scope-boundary-vs-messaging inconsistency (coherence P2) — addressed by R10 revision (copy + visuals ship together).

---

## Next Steps

-> `/ce-plan` for structured implementation planning.
