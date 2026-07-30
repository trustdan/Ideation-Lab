---
type: meta
created: 2026-07-30
---
# Linking spec — quick reference

**Canonical spec: `CLAUDE.md` §5.3 (weave block) and §6 (linking rules).** This card is a
reminder, not an authority.

- Frontmatter drives the graph: `related:` (deliberate), `frameworks:` (provenance),
  `targets:` (challenges), `distilled-from:` (ideas), `theme:` (set by synthesizer).
- `/weave` regenerates the `<!-- weave:start -->…<!-- weave:end -->` block at the end of
  each note from those fields — nothing else ever edits that block, and it's removed when
  empty. Idempotent by contract.
- Session hubs (`[[2026-08-12-product-offsite]]`) are the only stable cross-session link
  targets. Numbered internals need path-qualified links.
- Generated links are vault-absolute with alias; your own lazy links are fine when unique.
