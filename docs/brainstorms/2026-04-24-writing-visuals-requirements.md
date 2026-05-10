---
title: /writing typographic visual extensions — requirements
date: 2026-04-24
status: requirements captured, ready for ce-plan
scope: cbkdi/design-system, /writing long-form surface
motivator: CBKDI writings post #1 (in-place AI) is the first piece to exercise /writing visuals beyond the already-specified chrome
constraint: fully inside the R13a rubric — zero pictorial imagery, zero figurative illustration, single purple accent beat
---

# /writing typographic visual extensions — requirements

## Summary

The `/writing` long-form vocabulary in `DESIGN.md` already specifies TOC sidebar, breadcrumb chrome, revision stamps, §-anchors, footnote typography, and a blockquote treatment with a primary-purple left border as the one color beat per article. It does not yet specify treatments for three patterns that the first real `/writing` post will need:

1. `<pre>` code-block treatment (for directory trees, config snippets, structural visuals)
2. Inline `<code>` treatment (for file paths, skill names, command names, configuration keys in running prose)
3. A *frame block* composition pattern (for side-by-side or stacked typographic diagrams that illustrate structural concepts without introducing imagery)

All three are typographic extensions that compose existing tokens and faces. None introduces a new primitive, a new hue, or pictorial content. They formalize patterns that will recur across `/writing` posts once the surface is in use.

## Motivation

`cbkdi-website/docs/brainstorms/2026-04-24-in-place-ai-brief.md` specifies three visuals for the first `/writing` post — a directory tree, a user-level vs project-level memory diagram, and a memory-stacking diagram. All three are load-bearing to the post's thesis, and all three are typographic by construction. They cannot render with current tokens without either reaching for imagery (a brand violation) or hand-rolling ad-hoc CSS in the post itself (drift and inconsistency across future posts).

Formalizing now has two compounding benefits: post #1 drafts against stable treatments instead of one-off styles, and every subsequent `/writing` post inherits the same visual grammar instead of reinventing it.

## Scope

**In scope:**

- Define `<pre>` / code-block treatment for `/writing` articles.
- Define inline `<code>` treatment for `/writing` prose.
- Define a *frame block* composition pattern using existing `card` / `card-dark` primitives, mono eyebrow chrome, hairline rules, and (optionally) the existing blockquote primary-purple left-border treatment for the single accent beat.
- Update `DESIGN.md`'s `/writing` long-form section with the new vocabulary, including markup examples and rationale.
- Update `tokens.css` if and only if new values are actually required (default stance: compose from existing tokens).
- Update the R13a rubric only if any of the additions exposes a gap in the existing must-haves / should-haves / must-not-haves.

**Out of scope:**

- Any form of pictorial imagery, photo, figurative illustration, or AI-generated imagery — prohibited by R13a and not reconsidered here.
- A second accent hue, any animation beyond the existing hairline reveal pattern, any elevation (shadow / blur).
- Treatments for marketing surfaces — these additions are `/writing` only. The marketing vocabulary is complete as of Phase 1.
- An image-generation pipeline — that effort is parked indefinitely for `/writing` and would only become relevant for off-brand surfaces (proposal covers, social cards, email headers), which are not the subject of this brainstorm.

## Proposed additions

### 1. Code block — `<pre>`

Used inside `/writing` articles for directory trees, file snippets, command snippets, configuration excerpts.

Requirements:

- Face: IBM Plex Mono (`var(--font-mono)`)
- Font size: slightly smaller than the reading body — aim around `0.9375rem` to `1rem` so mono sits comfortably inside Source Serif 4 prose without dominating.
- Line height: `1.55` — tighter than reading body (1.65) to emphasize code as a structural block, looser than the `1.45` of mono-caption because these blocks may run several lines.
- Background: `var(--color-surface)` / `var(--color-surface-dark)` — reuses the existing card surface pair so code blocks sit on the same layer as cards.
- Border radius: `var(--radius-card)` (12px).
- Padding: approximately `1rem` vertical, `1.25rem` horizontal; responsive via existing clamp pattern if needed.
- Overflow: horizontal scroll if content exceeds the reading measure; no soft-wrapping of code.
- Margin: matches the existing paragraph rhythm — roughly `1.5rem` top/bottom.
- Inline annotation: mono comments or arrows in `var(--color-text-mid)` inside the pre block are permitted and encouraged for directory trees. These annotations must not use the primary accent — the blockquote owns the one-beat-per-article rule.

Rationale: the code block shares surface, radius, and face with existing primitives. No new tokens are introduced. The only decision is the exact font size and padding; both should be chosen to sit comfortably inside Source Serif 4 reading prose without pulling attention away.

### 2. Inline `<code>`

Used in running prose for file paths (`CLAUDE.md`), skill names (`closeout`), command names, configuration keys, short identifiers.

Requirements:

- Face: IBM Plex Mono (`var(--font-mono)`)
- Font size: slightly smaller than surrounding reading body — around `0.9em` relative — so mono does not bulge the line height.
- Weight: `400`.
- Color: `var(--color-text)` — no color change from body prose; differentiation is by face only.
- Background: either none (pure face-contrast) or a very subtle surface tint via `var(--color-surface)` with `0.15em` horizontal padding and `var(--radius-hairline)` corners. Choice between no-background and subtle-tint is an open question — see below.
- Margin / kerning: enough horizontal breathing room that mono code sits cleanly in a line of serif prose (small `0.1em` padding on each side if no background; slightly more if tinted).

Rationale: face-only differentiation matches the rubric's non-color principle (active states by weight or non-color; code is the same principle applied to an identifier). A subtle surface tint is legible but risks reading as tech-blog pastiche; pure face-contrast is cleaner but may read as under-differentiated at small reading-body sizes. Decide during implementation by comp.

### 3. Frame block composition pattern

Used for typographic diagrams inside articles: side-by-side comparisons, stacked layers, before/after, user-level vs project-level, and similar structural visuals.

This is a *composition pattern*, not a new primitive. It combines:

- `card` / `card-dark` container for each framed region
- A mono eyebrow label (`typography.eyebrow`) at the top of each frame naming what the frame represents (`USER LEVEL`, `BEFORE`, `YOUR BASELINE FILES`, etc.)
- Hairline rules or mono captions between frames when a relationship needs to be named (migration direction, stacking, sequence)
- Optional: the existing blockquote primary-purple left-border for a single emphasized layer, reusing the one-accent-beat-per-article rule

Requirements:

- Layout: stack vertically by default; side-by-side at the `/writing` reading measure only when both frames are short enough to avoid column compression.
- No new border colors, no new radii, no shadows, no gradients.
- Mono eyebrow labels sit above each frame, not inside the card body.
- Relationship captions (`→ closeout / dream`, `augments`, `replaces`) in mono at `var(--color-text-lt)`, 0.04em tracking, uppercase optional.
- Maximum one frame per article uses the blockquote-purple treatment; otherwise the article risks exceeding the single-beat rule.

Rationale: the frame block is a recipe, not a new component. Post #1 needs visuals 2 and 3 to render typographically, and both are expressible by composing primitives that already exist. Formalizing the recipe in `DESIGN.md` prevents drift across future posts.

## Constraints (restated)

- R13a must-not-have: no pictorial logos, icons-as-decoration, photos, figurative illustration, generated imagery
- R13a must-have: single purple accent used sparingly — one beat per screen-height, one blockquote-style accent per article
- No second hue, no elevation, no shadow, no blur
- No departure from the existing three-face system (Instrument Serif / Source Serif 4 / Inter / IBM Plex Mono)

## Open questions

1. **Inline `<code>` background:** pure face-contrast or subtle surface tint? Decide by comp during implementation.
2. **Code block font size relative to reading body:** `0.9375rem` or `1rem`? Comp both against a prose paragraph and pick the one that reads as *structural* rather than *loud*.
3. **Frame block at narrow viewports:** when both frames are too long for a side-by-side layout, how exactly do they stack? Vertical stack is the default answer; confirm at implementation time.
4. **Does the R13a rubric need a new must-have item** — e.g., "typographic-only visuals in `/writing`" — or is it already covered by the existing must-not-have against figurative illustration? Review during implementation.
5. **Annotation color inside code blocks:** `text-mid` or `text-lt`? Either is compliant; pick by legibility comp.

## Next step

Hand this to `ce-plan` to produce an implementation plan for a single PR into `cbkdi/design-system` covering:

- `DESIGN.md` `/writing` section updates for the three patterns above
- `tokens.css` additions (only if any are actually required)
- Rationale notes mirroring the structure of existing `/writing` vocabulary entries
- Specimen comps under `docs/comps/2026-04-24-writing-visuals/` (HTML comp set analogous to the `2026-04-24-faces` comps) showing each treatment in light and dark, mobile and desktop

Post #1 can draft against stubbed treatments in `cbkdi-website` (an internal class or two in `global.css`) without blocking on the full design-system extension. The extension PR can land after the first `/writing` post ships.

## Addendum 2026-05-06: syntax-highlighting in `<pre>` blocks

Surfaced during the second `/writing` post (*The agent that doesn't sleep*, cbkdi-website PR #16). The Rocky article's schema examples were originally tagged ` ```markdown ` to signal content type to the reader, but Shiki's default markdown theme emits a saturated blue for headings, bold markers, and link syntax that clashes hard with the brand-purple accent in the `/writing` chrome (active TOC item, blockquote left border).

The post-level workaround was to drop the language tag (` ```text `), which removes Shiki tokenization entirely and renders all-mono text in `var(--color-text)`. This works for the Rocky post because the schema examples read as content, not code. But it is a workaround, not a system answer. The first post that genuinely benefits from highlighted JSON, YAML, JS, or shell will hit the same clash.

### New requirement: syntax-highlighting palette

Add a fourth pattern to the in-scope list — a token-color treatment for syntax-highlighted code blocks that respects the rubric.

Constraints:

- The single primary-purple accent beat per article is owned by the blockquote left border. Syntax tokens MUST NOT use the primary purple, since that would multiply the accent.
- All other token colors must avoid hues outside the existing system. The current palette uses brand-purple as the only chromatic accent against neutrals; introducing Shiki's default rainbow (blue, red, green, yellow, magenta) is a rubric violation.
- Implication: tokens differentiate by **value** (light / mid / dark neutrals) and **weight** (regular / medium / semibold), not by hue. Comments stay at `var(--color-text-lt)`. Strings, identifiers, and operators distinguish via face-weight or value differences within the neutral ramp.
- Light and dark mode parity required, same as existing chrome.

### Implementation paths to weigh during ce-plan

1. **Configure Shiki with a custom theme** generated from existing tokens — produces a JSON theme file and a CSS variable mapping. Highest fidelity but most work.
2. **Override Shiki's emitted token colors via CSS** — leaves Shiki's class names in place but reassigns colors to brand neutrals through the existing CSS-variable system. Lower-effort, lower-fidelity.
3. **Disable Shiki for `/writing` and use unhighlighted `<pre>`** — purest neutral treatment but loses the legibility benefit of token differentiation in long code blocks. Probably wrong for posts with substantial code content.

Default lean: option 2 for the first iteration, with option 1 as the next step if value-only differentiation reads as too flat once we comp it.

### Open questions appended

6. **Token differentiation strategy:** value-only, weight-only, or value-and-weight combined? Comp during implementation against representative `markdown`, `yaml`, `json`, `js`, and `shell` blocks.
7. **Comment handling:** italic + `text-lt`, or roman + `text-lt`? Italic in IBM Plex Mono reads as deliberate; comp both.
8. **Existing post:** The Rocky article ships with the post-level workaround (` ```text ` for what would normally be ` ```markdown `). Once this requirement is implemented, the article can be re-tagged in a follow-up commit, or left as-is if the value-only treatment of `markdown` looks indistinguishable from plain text. Decide during implementation.
