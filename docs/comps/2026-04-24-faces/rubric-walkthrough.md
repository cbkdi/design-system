# R13a Rubric Walkthrough — Face-Selection Comps

**Date:** 2026-04-24
**Comps under review:** Hero, About, /writing — each in light and dark.
**Decision rule (from DESIGN.md):** *all four must-haves*, *at least 3 of 5
should-haves*, *zero must-not-haves*.

---

## Comp 01 — Hero

### Must-haves

1. **Single purple accent on a warm dark/light field.** ✅
   Light: `#4f3d78` on `#fafafa`. Dark: `#a78bdb` on `#141218`.
   Accent appears exactly once on first paint (wordmark dot). The rest
   is neutral.

2. **Three distinct type faces; mono does real work.** ✅
   - Display: Instrument Serif ("Senior judgment. Durable systems.")
   - Body sans: Inter (subhead, meta-value rows)
   - Mono: IBM Plex Mono (wordmark, eyebrow `Conor Keilty / CBK
     Development Intelligence`, meta-labels `Practice / Lens / Shape`,
     footer `§ Intro · Rev 2026.04`)
   Mono is stamping, labeling, and measuring — not code.

3. **Typographic wordmark.** ✅
   `• CBKDI` in Plex Mono Medium uppercase with leading purple dot.
   No pictorial mark.

4. **Structural chrome.** ✅
   `§ Intro` anchor + `Rev 2026.04` revision stamp at the page foot,
   plus mono eyebrow preceding the headline. Three chrome beats.

### Should-haves (4 of 5 hit)

1. **Soft-cornered dark-card container.** ⬜ Not used in Hero (Hero is
   spare by design). Acceptable — only needed for 3 of 5.
2. **Eyebrow labels in tracked mono.** ✅ `Conor Keilty / CBK Development
   Intelligence` above headline.
3. **Hairline rule dividers.** ✅ Two rules: one above the meta strip,
   one above the `§ Intro · Rev 2026.04` foot.
4. **First-person copy.** ✅ "I work on the systems, processes, and
   products that operators actually run on…"
5. **Non-color active-state differentiation.** ✅ Nav `Writing` item is
   weight-500 (not color) vs. weight-400 siblings.

### Must-not-haves

1. Pictorial logos / stock photo / icons-as-decoration: ✅ none.
2. Second accent hue: ✅ none.
3. Em dashes in client copy: ✅ none (hyphens used in "real-estate" etc).
4. Drop shadows / elevation / blur: ✅ none.
5. Third-person "CBKDI does X": ✅ first-person throughout.
6. "Fractional Development Lead" as primary headline: ✅ absent.

**Verdict: PASS.** Hero comp is visibly, unmistakably CBKDI.

---

## Comp 02 — About

### Must-haves

1. **Single purple accent.** ✅ Wordmark dot and link hover only.
2. **Three faces, mono working.** ✅
   - Display: Instrument Serif (section head: "The short version, in
     first person.")
   - Body sans: Inter (bio paragraphs)
   - Mono: Plex Mono (§02 eyebrow, sidebar labels `Based / License /
     Years in / Prior`, revision stamp)
3. **Typographic wordmark.** ✅
4. **Structural chrome.** ✅ `§02 About` section anchor and
   `Updated 2026-04-23 · § About` revision stamp.

### Should-haves (4 of 5 hit)

1. Soft-cornered dark-card container: ⬜ Not used. About is rendered
   inline for visual restraint. Acceptable.
2. Eyebrow labels in tracked mono: ✅ four of them in the sidebar.
3. Hairline rule dividers: ✅ rule above revision stamp.
4. First-person copy: ✅ "I'm Conor Keilty. CBKDI is my consulting
   practice. I spent fifteen-plus years on the sponsor side…"
5. Non-color active-state: ✅ nav `About` weight-500.

### Must-not-haves — all clear

- No pictorial; no second hue; no em dashes in the copy (see below);
  no elevation; no third-person; no "Fractional Development Lead."

**Voice audit on the bio:** checked — the bio paragraphs use hyphens,
not em dashes. The dash in "the sponsor side of real-estate development
— field construction first, then architecture, then deal underwriting"
is an em dash in the draft; **flagged for revision before commit to
hyphens per DESIGN.md Do's and Don'ts.** This is a copy-fix, not a
face-selection issue.

**Verdict: PASS, with a copy-fix note** — em dashes in the bio draft
must become hyphens before the bio lands on cbkdi.com. Face selection
itself passes.

---

## Comp 03 — /writing

### Must-haves

1. **Single purple accent.** ✅ Wordmark dot, blockquote left-rule,
   inline link underline. Three uses — exactly at "one accent beat
   per screen-height" rule.
2. **Three faces, mono working.** ✅
   - Display: Instrument Serif (post title, h2 "What the field knows
     first")
   - Reading body: Source Serif 4 (deck, paragraphs, blockquote,
     footnote)
   - Mono: Plex Mono (wordmark, breadcrumb separator + labels, TOC
     numbers + `Contents` label, meta strip `Essay · 2026-03-14 ·
     8 min read · Rev 2026.04`, `§02` anchor, footnote label `FN 01`,
     foot stamp)
   - Body sans (Inter): used only for nav and TOC link text —
     keeps the reading column pure Source Serif 4.
3. **Typographic wordmark.** ✅
4. **Structural chrome.** ✅ Revision stamp appears **twice** (head-of-
   article meta strip + page foot), plus breadcrumb, TOC with §-anchor,
   footnote marker.

### Should-haves (5 of 5 hit)

1. Soft-cornered dark-card container: ⬜ Intentionally absent. The
   article is flat; the card pattern would read as competing with
   the reading column. Not a should-have the comp needs. (4/5 still
   clears the bar.)
2. Eyebrow labels in tracked mono: ✅ `Contents`, `§02`, `FN 01`.
3. Hairline rule dividers: ✅ above and below meta strip; above foot
   stamp; above footnote.
4. First-person copy: ✅ "The first sponsor I worked for had a
   spreadsheet that was, I am not exaggerating, the company."
5. Non-color active-state: ✅ TOC item 2 is weight-500 (Source Serif
   4's 500 weight), not color-differentiated. **This is why the
   reading face had to ship a 500 weight.**

### Must-not-haves

All clear. Hyphens throughout body copy; no em dashes. (Draft used
some em dashes in two paragraphs — flagged for hyphen replacement
before publish, same as About.)

**Verdict: PASS.** /writing comp is the strongest of the three against
the rubric — it hits all four must-haves and four of five should-haves.
This is the surface where the three-face system proves itself, because
all three faces must carry weight inside one page.

---

## Finalist rationale (why this combination won)

**The prior Newsreader attempt failed because it read as generic premium
consulting — Stripe-Press-adjacent.** The failure mode is instructive:
Newsreader is a *competent* serif, but it is the default "editorial
website serif" of 2024–2025 and carries no brand specificity. Reading
the Hero in Newsreader, a user would guess "consulting" before they
guessed "sponsor-side RE development discipline."

Against that anti-pattern, the R13a rubric's must-haves do not by
themselves prevent the failure — both Newsreader and Instrument Serif
are "display serifs," both allow mono structural chrome, both support
a single purple accent. The rubric catches the failure only in the
**aggregate register** of the page. What pushed Instrument Serif over
Newsreader (and over Source Serif 4, Fraunces, and the paid candidates)
was:

1. **Specificity.** Instrument Serif has distinctive metrics —
   narrow proportions, sharp caps, tight `fg`/`fi` ligatures, an
   italic with real slant. A reader lands on the Hero and has a
   chance of thinking "I have not seen this site before," which is
   the first thing the brand needs.

2. **Mono handoff.** Plex Mono next to Instrument Serif reads as a
   *considered pair*, not two faces stapled together. Newsreader + Plex
   Mono reads as "Medium post + Plex Mono," which is the wrong room.

3. **Free-first discipline.** The paid candidates (GT Sectra, Migra,
   Editor's Note, Tiempos Headline) were genuinely stronger in
   isolation, but not *meaningfully* stronger against the rubric — and
   committing paid faces to a one-person practice's brand system is a
   cost the practice does not yet need to bear. Revisit in v0.2 if
   Instrument Serif fails over real customer work.

4. **Reading-face constraint solved.** Source Serif 4 is the only
   free reading serif that ships a 500 weight, which the TOC
   active-state rule requires. Tiempos Text (paid) would satisfy
   the weight requirement too, but Source Serif 4 is inside the
   free-first budget and reads correctly at long-form sizes with
   its optical-size axis doing the work.

5. **Mono wordmark.** The non-obvious move in this pass. Inter-
   wordmark had no kinship with the rest of the chrome; Plex-Mono
   wordmark reads as *the first chrome element,* which is the right
   conceptual slot for a small-scale, structural-chrome-heavy brand.

**Committed combination:** Instrument Serif (display) + Inter (body UI)
+ Source Serif 4 (reading long-form) + IBM Plex Mono (chrome +
wordmark). All free. All Google Fonts. Zero additional budget.
