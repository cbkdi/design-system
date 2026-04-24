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
  # Three-face system. COMMITTED 2026-04-24 (U6/U7/U10).
  # - Display: Instrument Serif (Google Fonts, OFL)
  # - Body:    Inter (retained)
  # - Reading: Source Serif 4 (Google Fonts, OFL) — /writing long-form only
  # - Mono:    IBM Plex Mono (Google Fonts, OFL)
  hero:
    fontFamily: Instrument Serif
    fontSize: 4.5rem
    fontWeight: 400
    lineHeight: 1.05
    letterSpacing: -0.015em
  section-head:
    fontFamily: Instrument Serif
    fontSize: 1.875rem
    fontWeight: 400
    lineHeight: 1.15
    letterSpacing: -0.005em
  body-lg:
    fontFamily: Inter
    fontSize: 1.0625rem
    fontWeight: 400
    lineHeight: 1.55
  body-md:
    fontFamily: Inter
    fontSize: 1rem
    fontWeight: 400
    lineHeight: 1.55
  body-sm:
    fontFamily: Inter
    fontSize: 0.875rem
    fontWeight: 400
    lineHeight: 1.5
  eyebrow:
    fontFamily: IBM Plex Mono
    fontSize: 0.75rem
    fontWeight: 500
    lineHeight: 1
    letterSpacing: 0.12em
  mono-caption:
    fontFamily: IBM Plex Mono
    fontSize: 0.75rem
    fontWeight: 400
    lineHeight: 1.45
    letterSpacing: 0.04em
  wordmark:
    fontFamily: IBM Plex Mono   # moved from Inter
    fontSize: 0.8125rem
    fontWeight: 500
    lineHeight: 1
    letterSpacing: 0.14em
  reading-body:
    fontFamily: Source Serif 4
    fontSize: 1.1875rem
    fontWeight: 400
    lineHeight: 1.65
  reading-h2:
    fontFamily: Instrument Serif
    fontSize: 2rem
    fontWeight: 400
    lineHeight: 1.15
    letterSpacing: -0.005em
  reading-h3:
    fontFamily: Instrument Serif
    fontSize: 1.4375rem
    fontWeight: 400
    lineHeight: 1.2

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

The three-face system does most of the brand identification work. All three are free (Google Fonts, OFL). No paid-face approval required for v1.

- **Display serif: Instrument Serif.** Narrow, high-contrast, with enough editorial attitude that the page does not read as "generic premium consulting." Committed 2026-04-24 after real-copy comps against Fraunces, Source Serif 4, and the prior Newsreader attempt. Fraunces read as design-Twitter; Source Serif 4 was correct but lacked the specificity the hero needs. Instrument Serif's single weight is a known constraint — accepted because display usage is always large and the italic covers deck copy and blockquotes. Used for `hero`, `section-head`, `reading-h2`, `reading-h3`.

- **Body sans: Inter.** Retained from v0.1. Quiet, readable, does not fight Instrument Serif above or IBM Plex Mono below. Used for marketing-surface body copy (`body-lg`, `body-md`, `body-sm`).

- **Reading body: Source Serif 4.** `/writing` long-form only. Ships a 500 weight, which is a hard requirement for the TOC active-item state (weight-based, not color-based — the non-color differentiator rule in R8a). Optical-size axis (8–60pt) means the face looks correct at reading-body size without the fake-italic slant some free serifs produce. Replaces the Inter fallback in v0.1. Used for `reading-body`; Instrument Serif still sets h2/h3 on `/writing` so the heading register reads unmistakably CBKDI.

- **Monospace: IBM Plex Mono.** Load-bearing for the "systems" signal. Chosen over JetBrains Mono (reads as IDE), Geist Mono (reads as Vercel), and Berkeley Mono (paid, $75/seat, not meaningfully stronger for our use — short labels and stamps, not body code). Plex Mono is explicitly typeset-for-print, which is the register this brand uses mono in. Used for `eyebrow`, `mono-caption`, `wordmark`, `revision-stamp`, breadcrumb separators, §-anchors, TOC numbers.

Rhythm notes:

- Instrument Serif is tighter than Georgia was. `--leading-display` is now `1.05`; hero tracks at `-0.015em` (not `-0.02em` — Instrument Serif's metrics are already tight).
- Source Serif 4 reads best at `leading-reading: 1.65` with the opsz axis allowed to find its own optical-size per font-size. Set `font-optical-sizing: auto` at `.reading-body`.
- Wordmark is now **mono**, tracked `+0.14em` uppercase — wider than the Inter version because Plex Mono's default letterfit is narrower. Eyebrow labels stay at `+0.12em` in mono.
- Font sizes in the front-matter are desktop caps. At narrower viewports, fluid `clamp()` values in `tokens.css` scale them down; the YAML documents the authored-for maximum.


## Layout

**Single container, single column, generous margins.** Max content width `1056px` (`66rem`). Frame padding clamps between `1.25rem` and `3rem` depending on viewport. Sections stack; rhythm comes from repetition, not grids-within-grids.

Section padding convention: `80px` top-and-bottom on desktop (the `section` spacing token), `64px` on mobile. This is the load-bearing vertical rhythm — keep it consistent across sections unless the section has a specific reason to deviate.

`/writing` surfaces adopt the same container. A left-column TOC sidebar appears at `≥1080px` (the `--breakpoint-reading` token), which sits above the content-max of `1056px` to avoid the 1024–1056px dead zone where a sidebar would compress the reading column. Below `1080px`, the TOC collapses into a top-of-post drawer.

Dividers are hairline rules in `rule` / `rule-dark`, optionally animated on scroll (respect reduced-motion).


### /writing — long-form reading surface

`/writing` inherits the site container (`66rem` max, `1.25rem`–`3rem` clamp padding). The following vocabulary is specific to `/writing` and does not apply to marketing surfaces.

**Reading face.** Source Serif 4 at `--text-reading-base` (clamps `1.0625rem` → `1.1875rem`). Line-height `1.65`. `font-optical-sizing: auto`. Old-style figures on (`onum`). Kerning and standard ligatures on. No hyphenation — the reading column is wide enough that hyphenation reads as broken.

**Reading type scale.**

- `h1` (post title): Instrument Serif, `clamp(2rem, 1.6rem + 2vw, 3.25rem)`, `line-height: 1.05`, `letter-spacing: -0.005em`, `text-wrap: balance`.
- `h2`: `--text-reading-h2` (`1.5rem` → `2rem`), Instrument Serif, `line-height: 1.15`. Spaced `2.5rem` above, `1rem` below. Carries a `§NN` anchor in Plex Mono `0.6875rem` `0.06em` tracking, vertical-aligned `0.45em`, `0.75em` right-margin from the h2 text.
- `h3`: `--text-reading-h3` (`1.1875rem` → `1.4375rem`), Instrument Serif, `line-height: 1.2`. Spaced `2rem` / `0.75rem`.
- `deck` (subtitle under the h1): Source Serif 4 italic, `1.1875rem`, `line-height: 1.55`, `color: text-mid`.

**Reading measure.** `--reading-measure: 64ch` on the `<article>`. At 1.1875rem Source Serif 4 this yields ~65–75 characters per line, which sits inside the 45–75ch reading-science range (Bringhurst; MDN). The TOC sidebar does not eat into this measure; it sits to the left of the article in its own 12rem column.

**TOC sidebar.** `display: grid; grid-template-columns: 12rem 1fr; gap: 4rem;` at `@media (min-width: 1080px)` (`--breakpoint-reading`). Below 1080px, the TOC collapses to a top-of-post drawer (`<details>` element, closed by default, mono summary label `Contents`).

The TOC is `position: sticky; top: 2rem; align-self: start;`. Items are an ordered list (`<ol>`), one `<li>` per h2, zero indent, numbers rendered via `data-n="01"` attribute (not `list-style-type`) so they typeset in Plex Mono at the correct size and stay aligned when titles wrap. **Active-item state is `font-weight: 500`** — no color change, no left-border, no background. The active item darkens from `text-mid` to `text`. This is the non-color differentiator required by R8a and is the reason Source Serif 4 (which ships 500) is the committed reading face.

```html
<ol>
  <li><a href="#s1" data-n="01">Section title</a></li>
  <li><a href="#s2" data-n="02" aria-current="true">Active section</a></li>
</ol>
```

**Breadcrumb.** Above the article, below the site header. Plex Mono `0.75rem`, `0.06em` tracking, uppercase, `text-lt` color. Separator is mono `/` in `rule` color with `0.6em` left/right margin. **Truncation:** breadcrumb items with rendered text over `40ch` get middle-segment ellipsis: `a…z` where `a` is the first 18ch and `z` is the last 18ch. Current-page item is `<span aria-current="page">`, never truncated — it can soft-wrap to a second line.

```html
<nav aria-label="breadcrumb" class="writing-breadcrumb">
  <a href="/">Home</a>
  <span class="sep">/</span>
  <a href="/writing">Writing</a>
  <span class="sep">/</span>
  <span aria-current="page">Post title here</span>
</nav>
```

**Revision stamp.** On every `/writing` post. Placed in a `writing-meta` rule-bordered strip immediately after the `deck` and immediately before the first body paragraph. Plex Mono `0.6875rem`, `0.08em` tracking, uppercase, `text-lt`. Contains: kind (`Essay` / `Note` / `Log`), publication date `YYYY-MM-DD`, read-time `N min read`, and revision stamp `Rev YYYY.MM`. Separated by `·` in `rule` color.

A second revision stamp appears at the page foot alongside the section marker (`CBKDI · § Writing` left, `Updated YYYY-MM-DD` right). The head-of-article stamp is load-bearing for reader trust; the foot stamp closes the document.

**Footnote typography.** Inline footnote marks are superscript numerals using Source Serif 4's built-in `sups` feature (not `<sup>` + `font-size`). Link color, `0.1em` left padding from the preceding word. Footnote body is Source Serif 4 `0.9375rem`, `line-height: 1.55`, `color: text-mid`, prefixed with a Plex Mono label `FN 01` in `0.75rem`, `0.04em` tracking, `text-lt` color, `0.5em` right-margin from the footnote prose. Footnotes sit at the end of the article, separated by a hairline rule, not inline at page-bottom — long-form `/writing` is for readers who tolerate a scroll, not for print.

**§-anchor rule.** Use on `h2` only, and only when the post has three or more h2 sections. A post with a single h2 gets no §-anchor — the anchor is doing navigational work that a single-h2 post does not need. Never used on h3.

**Blockquote.** Source Serif 4 italic, base reading size, left border `2px solid var(--color-primary)`, `1.25rem` left padding, `2rem` vertical margin. `color: text-mid`. This is the only place the purple accent appears inside an article body — one beat per quote.

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

`• CBKDI` — typographic only, no pictorial mark. **IBM Plex Mono Medium (500), uppercase, tracked `+0.14em`.** Leading purple dot (`0.4em`, `rounded.pill`, `colors.primary` on light / `colors.primary-dark` on dark), `aria-hidden="true"` on the dot.

**Rationale for the mono wordmark (committed 2026-04-24, U7):** Against Instrument Serif, a sans-serif wordmark read as visually unrelated — the display face and the wordmark had nothing in common. Moving the wordmark to Plex Mono puts it in the same family as the eyebrow labels, revision stamps, breadcrumbs, TOC numbers, and §-anchors, so every piece of structural chrome on the page shares one face. The wordmark now reads as *the first chrome element*, not as a separate logotype. The leading purple dot stays — it's the single piece of brand color on first paint and it punctuates the otherwise all-mono line cleanly.

**Markup:**

```html
<a href="/" class="wordmark" aria-label="CBKDI">CBKDI</a>
```

```css
.wordmark {
  font-family: var(--font-mono);
  font-size: 0.8125rem;       /* 13px header default */
  font-weight: 500;
  line-height: 1;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--color-text);
  display: inline-flex;
  align-items: center;
  gap: 0.55em;
}
.wordmark::before {
  content: "";
  width: 0.4em;
  height: 0.4em;
  border-radius: var(--radius-pill);
  background-color: var(--color-primary);
}
```

**Sizes:** defaults to `0.8125rem` (13px) in the Header. Scales down to `0.75rem` (12px) for footer chrome and up to `1rem` (16px) if ever used as a standalone mark. Never used above 1rem — the wordmark is chrome, not display.

**Do not** set the wordmark in the display face. Plex Mono is the committed treatment; a display-face wordmark was considered and rejected because it made the wordmark compete with the hero headline for visual weight.


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
- **Don't** set the wordmark in the display face or body sans. It is IBM Plex Mono, Medium, uppercase, tracked — every time.

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
- **Do** use the §-anchor rule: h2 only, only when a post has three or more h2 sections. Under that bar, the anchor is decoration, not navigation.

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
