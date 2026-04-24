# CBKDI Design System

The brand system for [CBKDI](https://cbkdi.com) (CBK Development Intelligence), a one-person consulting practice working on systems, process, and product design through a sponsor-side real-estate-development lens.

This repository is the single source of truth for CBKDI's visual identity. It holds:

- **`tokens.css`** - authoritative Tailwind v4 `@theme` token set (colors, typography, spacing, shape, motion). Light + dark modes in one file. Consumed at build time by [cbkdi.com](https://github.com/cbkdi/cbkdi-website) and any future CBKDI surface.
- **`DESIGN.md`** - canonical brand specification with YAML front-matter that mirrors `tokens.css`, plus prose describing intent, voice, and do's and don'ts. Consumed by [Claude Design](https://claude.ai/design) and by human implementers.

## How Claude Design consumes this

Hand the repo URL (plus a short intake blurb - see `DESIGN.md`) to Claude Design's intake surface. Claude Design fetches `DESIGN.md`, parses the YAML front-matter as design tokens, and reads the prose as design rationale. Output should be visibly, unmistakably CBKDI - the rubric for "visibly CBKDI" lives in `DESIGN.md` itself.

## Adoption path for CBKDI surfaces

1. Copy `tokens.css` from this repo at a specific commit SHA into the target project's styles directory.
2. Prepend a comment noting the source and SHA (e.g., `/* Vendored from cbkdi/design-system@<sha> */`).
3. Import `tokens.css` above the Tailwind import in the project's global stylesheet.
4. Refresh by repeating step 1 at a new SHA when tokens change. No runtime fetch, no submodule, no npm dep.

The [cbkdi.com site repo](https://github.com/cbkdi/cbkdi-website) is the reference implementation.

## Validation

```bash
npm install
npm run lint
```

Runs [`@google/design.md lint`](https://github.com/google-labs-code/design.md) against `DESIGN.md`. CI runs the same on every push.

## License

Apache License 2.0. Inherited from the upstream [`google-labs-code/design.md`](https://github.com/google-labs-code/design.md) project this repo was forked from.

## Format origin

This repository uses the [DESIGN.md format](https://github.com/google-labs-code/design.md) published by Google Labs. The format, lint tooling, and spec are upstream; the brand content here is CBKDI's.
