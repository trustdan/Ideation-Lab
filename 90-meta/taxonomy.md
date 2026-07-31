---
type: meta
created: 2026-07-30
---
# Taxonomy — controlled vocabulary

The schema (which fields exist, where required) is defined in `CLAUDE.md` §5.2. This file
defines the **allowed values**. Agents validate against this file. Forks: extend the lists
below freely; renaming or removing a value requires a vault-wide grep + `/weave --check`.

## type
`session` · `agenda` · `capture` · `idea` · `challenge` · `synthesis` · `actions` · `retro`
· `framework` · `scenario` · `meta` · `decision` · `test-scenario` · `prep-checklist`
· `follow-through`

Pack-level vs. per-day: `prep-checklist` and `follow-through` live in `20-scenarios/<pack>/`
and carry `scenario:`; `decision` and `test-scenario` live in a session and carry `session:`.

## phase
`diverge` · `converge` · `decide` · `commit`

## status — by type
- **session:** `planned` → `active` → `synthesized` → `closed`
- **idea:** `seed` → `shaped` · `parked` · `committed`
  (`committed` requires a matching entry in the session's `50-actions.md`)
- **actions item (inline):** `open` · `done` · `dropped`
- **framework:** `seed` (stub created by facilitator) · `ready`
- **prep-checklist:** `drafting` → `ready` · `blocked`
  (`ready` requires every gating item — decider, recruits, room — confirmed, not merely listed)
- **follow-through:** `open` → `tracking` → `closed`

## challenge verdicts
`proceed` · `reshape` · `park`

## test-scenario verdicts
`pending` · `validated` · `refuted` · `inconclusive`
(anything but `pending` requires ≥1 wikilink in `evidence:`)

## decision methods
`straw-poll` · `supervote` · `consensus`

## attribution (session hub field)
`anonymous` (default when absent) · `open`

## tags
Lowercase-kebab, topical only. Don't encode type/phase/status in tags — those are fields.
Prefer few and reused over many and precise.
