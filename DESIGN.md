---
version: alpha
name: CBKDI
description: >
  CBKDI (CBK Development Intelligence) is a one-person consulting practice.
  The brand expresses editorial voice inside opinionated structural chrome,
  set in a warm dark near-black field with a single purple accent. First-
  person voice, hyphens not em dashes, restraint over flourish.

colors:
  # Primary palette is a single purple accent on a neutral warm-dark ground.
  # The linter requires `primary`. Everything else is CBKDI-named.
  #
  # Naming convention: light-mode values are the base slot name; dark-mode
  # equivalents carry a `-dark` suffix. Components bind to the correct pair
  # through variant naming (e.g., `link` + `link-dark`). This lets the
  # linter's contrast rule check one palette at a time.

  primary: "#4f3d78"
  primary-dark: "#a78bdb"
  primary-hover: "#3d2e62"
  primary-hover-dark: "#c0a8f0"

  bg: "#fafafa"
  bg-dark: "#141218"

  surface: "#f2f1f4"
  surface-dark: "#1f1d24"

  text: "#1a1a1a"
  text-dark: "#e5e5e5"
  text-mid: "#4a4a4a"
  text-mid-dark: "#aaaaaa"
  text-lt: "#6e6e6e"
  text-lt-dark: "#808080"

  rule: "#dddddd"
  rule-dark: "#2a2a2a"

  error: "#b4232c"
  error-dark: "#f07a82"

typography:
  # Three-face system. Display and mono faces are v0.1 placeholders pending
  # face selection in U6 of the 2026-04-23 plan. Sizes shown are the
  # desktop cap of the fluid clamp() range authored in tokens.css; prose
  # below documents the fluid behavior.
  hero:
    fontFamily: Georgia
    fontSize: 2.5rem
    fontWeight: 600
    lineHeight: 1.1
    letterSpacing: -0.02em
  section-head:
    fontFamily: Georgia
    fontSize: 1.5rem
    fontWeight: 600
    lineHeight: 1.2
  body-lg:
    fontFamily: Inter
    fontSize: 1.0625rem
    fontWeight: 400
    lineHeight: 1.6
  body-md:
    fontFamily: Inter
    fontSize: 1rem
    fontWeight: 400
    lineHeight: 1.6
  body-sm:
    fontFamily: Inter
    fontSize: 0.875rem
    fontWeight: 400
    lineHeight: 1.5
  eyebrow:
    fontFamily: JetBrains Mono
    fontSize: 0.75rem
    fontWeight: 500
    lineHeight: 1
    letterSpacing: 0.12em
  mono-caption:
    fontFamily: JetBrains Mono
    fontSize: 0.75rem
    fontWeight: 400
    lineHeight: 1.45
    letterSpacing: 0.04em
  wordmark:
    fontFamily: Inter
    fontSize: 1rem
    fontWeight: 600
    lineHeight: 1
    letterSpacing: 0.08em
  reading-body:
    fontFamily: Inter
    fontSize: 1.125rem
    fontWeight: 400
    lineHeight: 1.7
  reading-h2:
    fontFamily: Georgia
    fontSize: 1.75rem
    fontWeight: 600
    lineHeight: 1.2
  reading-h3:
    fontFamily: Georgia
    fontSize: 1.3125rem
    fontWeight: 600
    lineHeight: 1.3

rounded:
  hairline: 2px
  card: 12px
  pill: 9999px

spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 32px
  2xl: 48px
  3xl: 64px
  section: 80px
  max-content: 1056px

components:
  wordmark:
    typography: "{typography.wordmark}"
    textColor: "{colors.text}"
  wordmark-dark:
    typography: "{typography.wordmark}"
    textColor: "{colors.text-dark}"

  link:
    textColor: "{colors.primary}"
  link-hover:
    textColor: "{colors.primary-hover}"
  link-dark:
    textColor: "{colors.primary-dark}"
  link-hover-dark:
    textColor: "{colors.primary-hover-dark}"

  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.bg}"
    rounded: "{rounded.pill}"
    padding: 12px
  button-primary-hover:
    backgroundColor: "{colors.primary-hover}"
    textColor: "{colors.bg}"
  button-primary-dark:
    backgroundColor: "{colors.primary-dark}"
    textColor: "{colors.bg-dark}"
    rounded: "{rounded.pill}"
    padding: 12px

  card:
    backgroundColor: "{colors.surface}"
    rounded: "{rounded.card}"
    padding: 24px
  card-dark:
    backgroundColor: "{colors.surface-dark}"
    rounded: "{rounded.card}"
    padding: 24px

  revision-stamp:
    typography: "{typography.mono-caption}"
    textColor: "{colors.text-lt}"
  revision-stamp-dark:
    typography: "{typography.mono-caption}"
    textColor: "{colors.text-lt-dark}"

  field-focus:
    textColor: "{colors.primary}"
  field-focus-dark:
    textColor: "{colors.primary-dark}"
  field-error:
    textColor: "{colors.error}"
  field-error-dark:
    textColor: "{colors.error-dark}"

  body-mid:
    typography: "{typography.body-md}"
    textColor: "{colors.text-mid}"
  body-mid-dark:
    typography: "{typography.body-md}"
    textColor: "{colors.text-mid-dark}"

  divider:
    backgroundColor: "{colors.rule}"
    height: 1px
  divider-dark:
    backgroundColor: "{colors.rule-dark}"
    height: 1px
---

# CBKDI

## Overview

### Who this is for

CBKDI is [Conor Keilty](https://cbkdi.com). One person. Licensed architect, fifteen-plus years across field construction, architecture, and sponsor-side real-estate development. The practice works on systems, process, and product design viewed through that RE-development lens. Fractional development-lead work is still on the menu but is no longer the headline.

### Personality

**Editorial voice inside opinionated structural chrome.** The visual feel borrows from editorial design (Ink & Switch, Linear's docs, New York Times morning briefings, engineering blogs that still read like writing) and runs it inside the deliberate typographic chrome of [02ui.com](https://02ui.com), translated away from 02ui's pixel-art costume. Text leads. Structure supports it. The accent purple is the single emotional beat; everything else is neutral.

**Not** premium-restrained consulting polish (Stripe Press, Palantir-adjacent). **Not** startup-bright. **Not** pictorial. **Not** illustrated.

### Claude Design intake blurb

> CBKDI (cbkdi.com) is my consulting practice. I work on systems, process, and product design for operators who need judgment more than they need another spreadsheet, drawing on fifteen years of sponsor-side real-estate development. The visual language is editorial voice inside opinionated structural chrome: first-person copy, restrained purple accent on warm dark, three-face typography (display serif + Inter + mono), soft-cornered dark cards, hairline rules, revision stamps, sparing §-anchors. Set in the system defined by this repository.

This blurb is authored to be pasted into `claude.ai/design` alongside the repository URL. It is revised in lockstep with the Hero copy; if you change the positioning sentence on cbkdi.com, revise this blurb in the same commit.

## Colors

The palette is deliberately narrow. One accent hue, one neutral scale, two paired surfaces. No secondary brand color, no tertiary hue — scarcity is the point.

- **Primary (`#4f3d78` light / `#a78bdb` dark):** A deep purple used for accents, links, focus rings, and the wordmark dot. On light the value is saturated and authoritative; on dark it lifts to stay readable on warm near-black. It is the only non-neutral in the system.

- **Warm dark ground (`#141218`):** A deliberate shift off pure `#111111`. The slight purple tint reads as intentional and pairs with the accent rather than competing with it. The card surface `#1f1d24` sits one step above the page.

- **Light ground (`#fafafa`):** A hair warmer than `#ffffff`, enough to read as "paper" rather than "screen." Paired with a card surface of `#f2f1f4`.

- **Neutral grays (`text`, `text-mid`, `text-lt`):** Carry every body-copy tier, caption, rule, and disabled state. They are not brand colors; they are the calm field the purple accent operates against.

- **Error (`#b4232c` light / `#f07a82` dark):** A specific CBKDI red for form validation. Decoupled from browser-default red so the palette reads as intentional.

Contrast is verified for each paired token against its matched surface at WCAG AA. See the "Design Tokens" YAML front-matter for exact values.

## Typography

The three-face system does most of the brand identification work.

- **Display serif (`hero`, `section-head`, `reading-h2`, `reading-h3`):** Carries headlines. Currently a placeholder (`Georgia`) pending face selection against CBKDI's actual copy. Candidates include Fraunces, Instrument Serif, Source Serif 4, GT Sectra. The chosen face must feel editorial, not academic-conservative — it should look like it belongs next to the kind of writing Conor would publish, not next to a law-firm prospectus.

- **Body sans (`body-lg`, `body-md`, `body-sm`, `wordmark`):** Inter, retained from the prior site. Competent, quiet, and does not fight the display face.

- **Monospace (`eyebrow`, `mono-caption`):** Structural chrome — revision stamps, eyebrow labels that precede section headings, breadcrumb separators, TOC markers on `/writing`. Currently placeholder (`JetBrains Mono`). Candidates include Berkeley Mono (paid), Geist Mono, IBM Plex Mono. The mono is load-bearing for the systems signal; if it reads as dev-docs, the whole system does.

- **Reading body (`reading-body`) — `/writing` surface:** Currently Inter. A reading serif (Source Serif 4, Tiempos Text) may replace it once real long-form copy exists.

Rhythm notes:
- Display headings are tight (leading 1.1–1.2) and may carry negative letter-spacing on the hero (`-0.02em`).
- Body copy runs at leading 1.6; long-form reading body at 1.7 for a looser measure.
- Wordmark is tracked `+0.08em` uppercase. Eyebrow labels are tracked `+0.12em` uppercase in mono.
- Font sizes in the front-matter are desktop caps. At narrower viewports, fluid `clamp()` values in `tokens.css` scale them down; the YAML documents the authored-for maximum.

## Layout

**Single container, single column, generous margins.** Max content width `1056px` (`66rem`). Frame padding clamps between `1.25rem` and `3rem` depending on viewport. Sections stack; rhythm comes from repetition, not grids-within-grids.

Section padding convention: `80px` top-and-bottom on desktop (the `section` spacing token), `64px` on mobile. This is the load-bearing vertical rhythm — keep it consistent across sections unless the section has a specific reason to deviate.

`/writing` surfaces adopt the same container. A left-column TOC sidebar appears at `≥1080px` (the `--breakpoint-reading` token), which sits above the content-max of `1056px` to avoid the 1024–1056px dead zone where a sidebar would compress the reading column. Below `1080px`, the TOC collapses into a top-of-post drawer.

Dividers are hairline rules in `rule` / `rule-dark`, optionally animated on scroll (respect reduced-motion).

## Elevation & Depth

**Flat, deliberately.** No shadow tokens. No elevation scale. Hierarchy comes from:

- Surface pair (page bg vs. card surface) — the only "layer" concept in the system.
- Rule hairlines between sections.
- Typography scale + weight.
- Occasional §-anchor labels (sparing).

Shadows and blurs are reserved for flourishes that do not exist in the current system. This is an editorial-flat aesthetic. If a future surface proposes adding elevation, that proposal needs to justify why the existing flat hierarchy fails.

## Shapes

Soft-cornered containers, hairline rules, tight geometry.

- **Card radius:** `12px` (`rounded.card`). Applied to dark-card containers, the about-block surface, and any future grouped content blocks. Soft enough to read as intentional; not so soft as to drift toward rounded-everything web-app aesthetic.
- **Pill radius:** `9999px` (`rounded.pill`). Applied to ThemeToggle, primary buttons, chip tags ("In the Room" tags), and any full-round ends.
- **Hairline radius:** `2px` (`rounded.hairline`). Applied to focus rings and thin chrome elements.
- **§-anchors:** small mono labels (e.g., `§02`) sit inline with h2/h3 in long-form. Used sparingly on `/writing` surfaces; do not use on marketing surfaces.

### 02ui moves borrowed

Enumerated here per requirement R5a of the origin brainstorm. CBKDI borrows these specific moves from [02ui.com](https://02ui.com), translated away from 02ui's pixel-art and arcade aesthetic into an editorial register:

1. **Three-face type system with monospace as structural chrome.** Mono is not code-formatting; it labels, stamps, and measures.
2. **Accent-on-warm-dark palette** with a single hue, not a three-color system.
3. **Soft-cornered dark-card containers** that group content without pretending to be elevated surfaces.
4. **Uppercase + tracked mono labels** for eyebrows and chrome callouts.
5. **Breadcrumb / TOC / revision-stamp chrome** that makes the page feel like it has a known location in a larger system.
6. **Specific type-contrast register:** display serif sets an editorial tone, mono sets a systems tone, body stays quiet between them.
7. **Sparing §-anchor usage** — every time you see one, it's doing work.

CBKDI does not borrow 02ui's pixel art, retro-arcade illustrations, 8-bit-influenced spacing rhythm, or CRT scanline treatment. The translation from 02ui to CBKDI strips everything that reads as costume and keeps what reads as structure.

## Components

### Wordmark

`• CBKDI` — typographic only, no pictorial mark. Inter semibold, uppercase, tracked `+0.08em`. Leading purple dot (0.4em, `rounded.pill`, `colors.primary` on light / `colors.primary-dark` on dark), `aria-hidden="true"` on the dot. The dot may be retired or repositioned in U7 once the display face is chosen; do not treat the leading-dot pattern as locked.

Sizes: defaults to 1rem in the Header. Scales to 24px (email signatures, small chrome) and up to 72px (hero-adjacent, if ever used) without losing intent.

### Link

Default state: `colors.primary` (light) / `colors.primary-dark` (dark). Underline on hover (token hairline), with a `1px` underline offset so the text doesn't collide with the line.

Focus-visible: `2px` outline in the focus-ring color, `3px` offset, `rounded.hairline`.

Current-page marker (in header nav): non-color differentiator — weight-500 text OR a short hairline underline. Not color, so the page-context signal survives the dark-mode flip intact.

### Button — primary

`button-primary` in the YAML. Rounded pill (`rounded.pill`), 12px padding. Background = primary accent; text = page background. Hover darkens background to `primary-hover`. Focus-visible adds `2px` outline with `3px` offset.

Dark-mode variant: `button-primary-dark` swaps background to `primary-dark` and text to `bg-dark`.

### Card — dark-card container

Soft-cornered block (`rounded.card`, 12px). Background = `surface` / `surface-dark`. Padding 24px. No border, no shadow. Used for the About block and any future grouped content the editorial rhythm calls for.

### RevisionStamp

Mono caption at the page foot. `typography.mono-caption`, text color `text-lt` / `text-lt-dark` (low-contrast on purpose — metadata, not signal). Format: `REV YYYY.MM` or `Updated YYYY-MM-DD`, tracked slightly (`+0.04em` in mono-caption).

The one v1 chrome consumer on the public site — inserted in `BaseLayout` or `PageLayout` so every page carries it. Source: page front-matter `lastmod` if present, else git commit date of the page file.

### Breadcrumb (spec only, ships with `/writing`)

Future-surface chrome. `<nav aria-label="breadcrumb">` with `<ol>` > `<li>` > `<a>`. Separator: mono `/`. Last item: `<span aria-current="page">`. Truncation for long titles: middle-segment ellipsis at `≤ 40ch`. No Astro implementation in v1 — the component ships alongside the first real `/writing` post.

### TOC (spec only, ships with `/writing`)

Sidebar `≥1080px`, collapsible drawer below. Active-item state: **`font-weight: 500`** on current item (non-color differentiator, chosen over left-border so it survives mobile / drawer layout without padding-budget adjustment). Active requires that the chosen reading face ships a 500 weight — the selected display/reading face must carry this as a hard requirement.

### SectionAnchor (spec only, ships with `/writing`)

`<span>` with `id` and inline `§NN` label in mono, rendered alongside `h2`/`h3`. Used sparingly — if every section has one, none of them do work. Not present on marketing surfaces.

### ThemeToggle

The Svelte 5 rune-based toggle at `cbkdi-website/src/components/layout/ThemeToggle.svelte`. Hover states: `bg-[var(--color-neutral-200)]` / `dark:bg-[var(--color-neutral-800)]` — token-driven, replacing the prior `slate-200` / `slate-700` hardcodes. Focus-visible: standard ring. `pill` rounded.

### Contact form fields

`field-focus` + `field-focus-dark` for focus ring color. `field-error` + `field-error-dark` for validation error state (dedicated error token, not browser-default red). Disabled fields use reduced opacity (`0.5`) and `aria-disabled="true"`. Submit button uses `button-primary` + loading / success / error follow-on states (loading: disabled + text swap; success: inline confirmation; error: inline message in the error color).

### Reduced motion

Every chrome animation (link underline reveal, card hover, section divider scale-in) is wrapped in `@media (prefers-reduced-motion: no-preference)`. Reduced-motion users see the final state, no transition.

## Do's and Don'ts

### Voice

- **Do** write in first person. "I", not "CBKDI" or "Conor" in third person. The site is one person talking directly.
- **Do** use hyphens for inline clauses. Do not use em dashes anywhere in client-facing copy (emails, website, proposal bodies, DESIGN.md prose). This is a CBKDI-wide voice rule, not a design-system preference.
- **Do** lead positioning sentences with the verb-noun of what actually gets done. "Turning ambiguous operator problems into systems," not "Development intelligence for operators."
- **Don't** enumerate the three audiences (sponsor / platform-builder / construction owner) as separate service lanes. They are exemplars of one problem, not three products.
- **Don't** use the word "Fractional" in Hero copy. It is secondary service language, not the headline.

### Visual

- **Do** let text lead. Chrome is supporting structure, not a design feature to demonstrate.
- **Do** maintain WCAG AA contrast. The full token matrix is verified; custom off-palette colors do not get a free pass.
- **Do** use the purple accent sparingly. One accent beat per screen-height is a working rule.
- **Don't** introduce a second accent hue. If a second color feels needed, the layout or type is probably doing too little work.
- **Don't** mix the mono face with non-chrome text. Mono is for labels, stamps, captions, and separators — not body copy, not pull quotes.
- **Don't** add elevation (shadows, blurs, translucency) without a prose-justified reason. The default answer is flat.
- **Don't** use pictorial illustration. No stock photos, no icon sets acting as decoration, no figurative imagery. The wordmark and any future marks stay typographic.

### Chrome

- **Do** use §-anchors sparingly on `/writing`. Every anchor should do navigational work.
- **Do** include the `RevisionStamp` on every page so the site reads as a maintained document, not a static artifact.
- **Don't** stack multiple chrome elements vertically. Breadcrumb OR TOC header OR revision stamp in a given location, not all three.
- **Don't** remove the `RevisionStamp` to "clean up" a page. It is load-bearing for the editorial voice.

### The R13a rubric: visibly, unmistakably CBKDI

A design output passes the rubric — and qualifies as "visibly, unmistakably CBKDI" — when it meets **all must-haves**, **at least 3 of the 5 should-haves**, and **none of the must-not-haves.**

**Must-haves (all four required):**

1. Single purple accent (`colors.primary` / `colors.primary-dark`) used sparingly on a warm dark or warm light field. No other accent hues present.
2. Three distinct type faces evident: a display serif, a body sans (Inter or visually equivalent), and a monospace. The mono does real work (at least one label, caption, or stamp) — it isn't just code formatting.
3. Typographic wordmark, not pictorial. If a dot or punctuation mark accompanies "CBKDI," it reads as intentional typography, not as decoration.
4. Structural chrome present: at minimum, a revision stamp or editorial-metadata caption somewhere on the output.

**Should-haves (3 of 5):**

1. Soft-cornered dark-card container used to group content.
2. Eyebrow labels in uppercase tracked mono preceding section headings.
3. Hairline rule dividers between major sections.
4. First-person copy (or copy that reads as a single voice, not a corporate "we").
5. Active-state differentiation by weight or non-color means, not by color change alone.

**Must-not-haves (none allowed):**

1. Pictorial logos, icons-as-decoration, stock photography, or figurative illustration.
2. A second accent hue (green, blue, orange, etc.) at any saturation beyond incidental thumbnail imagery.
3. Em dashes in any client-facing copy (hyphens only).
4. Drop shadows, elevated-card effects, or translucent-blur surfaces.
5. Any third-person "CBKDI does X" construction in body copy.
6. "Fractional Development Lead" as the primary headline.

When evaluating a Claude Design or other agent-generated output against this rubric, a reviewer walks through each category. An independent reviewer applying this rubric to the same screenshot should reach the same verdict. If two reviewers disagree, the rubric itself gets sharpened — the ambiguity is a bug in the rubric, not a stylistic nuance.
