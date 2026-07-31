---
type: meta
created: 2026-07-31
---
# Design Sprint 2.0 beta — exit checklist

Consolidates the verification already run across `.claude/plans/design-sprint-beta-vault.md`
(Phases 0–4, done and committed at `54a7d27`) and this repo's own Phase 5. Doesn't restate
those phases' verification steps — see the plan file for the detail behind each line.

## Vault — Phases 0–4 (done)
- [x] Taxonomy carries `decision` / `test-scenario` / `prep-checklist` / `follow-through`, plus
  their status/verdict/method vocabularies (`90-meta/taxonomy.md`).
- [x] `CLAUDE.md` §5.2 documents every field those types introduced.
- [x] Four templates + one clean/one broken fixture each exist in `90-meta/templates/`.
- [x] `synthesizer.md` answers sprint questions and assigns `test-scenario` verdicts when
  present; doesn't require them when absent (proven on `2026-07-30-strategy-clinic`, which
  predates `test-scenario` notes and still synthesizes cleanly).
- [x] `coach.md` exists with prep / sideline / debrief modes and the rehearsal capability.
- [x] Five sprint framework notes exist and are registered in `10-frameworks/index.md`.
- [x] `90-meta/facilitator-growth-log.md` exists, seeded with one hand-written entry, with its
  own idempotency rule documented in its header.

## Vault — Phase 5 (this pass)
- [x] Scenario-hub template carries optional Long-term-goal / Sprint-questions sections (D4);
  `CLAUDE.md` §11 documents them and cross-references §5.2.
- [x] `export.md` pulls Sprint questions answered, Scenario verdicts, and `decision` notes when
  present, and states that `prep-checklist`/`follow-through` are pack-level and out of scope —
  verified additive by reading `2026-07-30-strategy-clinic`'s existing (pre-fix) export against
  its now-populated `40-synthesis.md` Scenario verdicts table.
- [x] `export.md` mirrored to `Ideation-Lab-Web` and committed there (`060a2f5`), touching only
  that one file.
- [x] `20-scenarios/design-sprint-2/` authored: hub, agenda-seed, prompt-pack,
  capture-templates, references.
- [x] `coach.md` prep mode dogfooded for real against the new pack, producing
  `prep-checklist.md` and `interview-script.md` — the first non-fixture invocation of Phase 3's
  agent.

## Not yet done (deliberately out of scope here)
- No real session has run against `design-sprint-2` yet — the hub's Long-term-goal/Sprint-
  questions sections are still illustrative placeholders, and `test-scenario` notes don't exist
  because no session exists to hold them. This is expected: they get created the first time
  someone runs `/new-lab` against this pack for a real engagement.
- The web portal's own Phase 0–4 (lint/contract-doc/drift-test, stage UI, CoachRail, Phase 2/4
  wiring) is owned by `Ideation-Lab-Web/.claude/plans/design-sprint-beta-web.md`, not this
  checklist. That repo currently has unrelated in-progress, uncommitted work on the coach route
  and `CoachRail` — untouched by this pass.
- `prep-checklist.md`'s `status` stays `drafting` by design until a human confirms every gating
  item for a real engagement (§7 taxonomy rule) — promoting it to `ready` is not a beta-exit
  criterion, it's a per-engagement one.
