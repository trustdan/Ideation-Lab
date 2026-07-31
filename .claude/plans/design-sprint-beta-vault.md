# Design Sprint Beta — Vault Implementation Plan (Phases 0–4)

**Repo:** `Ideation-Lab` (this one — the vault).
**Companion:** `Ideation-Lab-Web/.claude/plans/design-sprint-beta-web.md`.
**Source brief:** `Ideation-Lab-Web/docs/claude-upgrades-2.md` ("BETA-PLAN").

---

## Context

BETA-PLAN targets a Design Sprint 2.0 beta: four new note types, a BDD verdict thread through
synthesis, and a Coach agent. Its phases were written portal-first, which buries the fact that
most of the *unblocking* work is content and contracts — and those live here.

This vault is the source of truth. The portal is one consumer of it, not its owner. Every item
in this plan is therefore held to one standard:

> **Each phase must be independently valuable with the portal switched off.**

If a step only makes sense because a portal screen needs it, it belongs in the companion plan,
not here. Concretely: this plan authors taxonomy, templates, prompts, and framework notes — all
of which work in Claude Code and Obsidian today, with no server running.

**Phase numbering follows BETA-PLAN** so the two plans line up. **Phase 1 has no vault work** —
it is entirely portal lifecycle code — so it is absent below. That gap is intentional.

Per D8 this plan stops at **Phase 4**. Phase 5 (the authored Design Sprint 2.0 scenario pack)
is deferred to its own cycle; it is the largest content deliverable and cannot be specified
precisely until 0–4 exist.

---

## Shared contract (identical in both plan files)

- The **vault owns the taxonomy**. `Ideation-Lab-Web/lib/vault/lint.ts` is the enforcing
  mirror; `Ideation-Lab-Web/docs/vault-contract.md` is documentation that must match both.
  Where the three disagree, the vault wins.
- The **vault owns** `.claude/agents/*.md` and `.claude/commands/*.md`. The web repo's copies
  are deployed mirrors, guarded by a drift test (D7).
- The portal may propose writes **only** under `30-sessions/**` and `20-scenarios/**` (D6),
  `.md` only, no `..`, no leading `/`.
- **Pack-level** artifacts live in `20-scenarios/<pack>/`. **Per-day** artifacts live in
  `30-sessions/<slug>/`.
- The vault must remain fully usable with the portal switched off.

---

## Decisions this plan is built on

| # | Decision |
|---|---|
| D1 | Growth log is [90-meta/facilitator-growth-log.md](90-meta/facilitator-growth-log.md), append-only via Diff Review. |
| D2 | Session-per-day; Prep/Follow-through bracket the pack, not the day. |
| D3 | Rehearsal roleplay v1 runs **here**, via Claude Code, from `coach.md`'s prep-mode section. No portal surface. |
| D4 | Long-term goal + sprint questions are **prose sections** in the scenario hub, not structured frontmatter. `test-scenario` notes carry stable `id`s and link back. |
| D5 | Verdicts live in `test-scenario` note frontmatter. The portal parses them; nothing here depends on that. |
| **D6** | Pack-level artifacts live in `20-scenarios/<pack>/`. Per-day in `30-sessions/<slug>/`. |
| **D7** | This repo is canonical for prompts. See Mirror obligations below. |
| **D8** | Phases 0–4 only. |

---

## Phase 0 — Taxonomy & templates

*Blocks everything, in both repos. The portal's Phase 0 cannot start until this lands.*

### 0.1 Extend [90-meta/taxonomy.md](90-meta/taxonomy.md)

Add four values to the `## type` list: `decision`, `test-scenario`, `prep-checklist`,
`follow-through`. Add their vocabularies in the file's existing house style — terse, `·`-separated,
arrows for lifecycles:

- **`## status — by type`** gains entries for `prep-checklist` and `follow-through`.
- **A new `## test-scenario verdicts` section**, written to match the existing
  `## challenge verdicts` section exactly — that is the pattern to copy:
  `pending` · `validated` · `refuted` · `inconclusive`.
- **A new `## decision methods` section**: `straw-poll` · `supervote` · `consensus`.

Keep the file's opening note honest: it says the *schema* lives in `CLAUDE.md` §5.2 and this
file defines *allowed values*. Any genuinely new **field** (`method`, `decider`, `outcome`,
`rationale`, `made-during`, `sprint-question`, `verdict`, `evidence`) therefore also needs a row
in the `CLAUDE.md` §5.2 frontmatter table. **The overview missed this** — adding types to
`taxonomy.md` alone leaves the new fields undocumented.

### 0.2 Four new templates in [90-meta/templates/](90-meta/templates/)

Match the house style of the existing four ([idea.md](90-meta/templates/idea.md),
[challenge.md](90-meta/templates/challenge.md), [framework.md](90-meta/templates/framework.md),
[capture.md](90-meta/templates/capture.md)): YAML frontmatter with `{{placeholder}}` values,
an `# H1` title line, then bare `##` section headings with no filler prose. `challenge.md` is
the closest model for the section-heading style.

| File | Frontmatter | Body sections |
|---|---|---|
| `decision.md` | `type`, `session`, `method`, `decider`, `options` (wikilinks), `outcome`, `rationale`, `made-during`, `created` | `## Options considered` · `## Outcome` · `## Rationale` |
| `test-scenario.md` | `type`, `session`, `id`, `sprint-question`, `verdict: pending`, `evidence: []`, `created` | `## Given` · `## When` · `## Then` · `## Evidence` |
| `prep-checklist.md` | `type`, `scenario`, `status`, `created` | `## Recruit` · `## Decider` · `## Room & supplies` · `## Screener` |
| `follow-through.md` | `type`, `scenario`, `status`, `created` | `## Decisions` · `## Owners` · `## Next check` |

Note the split: `decision` and `test-scenario` carry `session:` (they are produced inside a
session); `prep-checklist` and `follow-through` carry `scenario:` instead, because per D6 they
live at pack level in `20-scenarios/<pack>/` and have no owning session.

### 0.3 Hand-write one valid sample of each type

Not shipped content — throwaway fixtures used to verify the portal's validators in its Phase 0.
Write one clean and one deliberately broken instance of each (a `supervote` decision missing
`decider`; a `validated` test-scenario with no evidence). Keep them out of `30-sessions/` so
they are not mistaken for real session content.

## Phase 2 — Synthesizer prompt: the verdict thread

*Depends on Phase 0. Content edit only — no code anywhere.*

Edit [.claude/agents/synthesizer.md](.claude/agents/synthesizer.md), preserving its existing
structure (`Inputs` / `Output` / `Procedure` / `Quality bar` / `Run report`) and its
`name` / `description` / `tools` frontmatter. Three additions:

1. **`## Inputs`** — also read the scenario hub's long-term-goal and sprint-question prose
   sections (D4), and every `test-scenario` note for the session's pack.
2. **`## Procedure`** — after clustering, check back against the anchors: answer every sprint
   question explicitly in `40-synthesis.md`, and assign each `test-scenario` a verdict of
   `validated | refuted | inconclusive` with at least one cited evidence wikilink.
3. **`## Quality bar`** — an unanswered sprint question or an unresolved scenario is a failed
   run, and a non-`pending` verdict without evidence is invalid.

Also update `30-sessions/_template/40-synthesis.md` with a `## Sprint questions answered`
section and a scenario verdict table, so the structure exists before an agent has to invent it.

**This is worth doing on its own merits**: it makes `/synthesize` answer the questions the
session was convened to answer, whether or not a portal ever renders a verdict chip.

## Phase 3 — Coach agent + sprint framework library

*Depends on Phase 0. Parallel with the portal's Phase 1.*

### 3.1 New `.claude/agents/coach.md`

Follow the existing six agents' convention: `name` / `description` / `tools` frontmatter, then
role prose. One file, three mode sections.

- **prep** — deep, file-producing. Drafts the prep checklist, interview screener,
  `test-scenario` notes, and five-act interview script.
- **sideline** — fast, ephemeral. Hard contract, stated in the prompt: **≤ one move plus one
  script line**; cite framework notes by name; never invent method steps; **never propose file
  writes** — anything write-shaped becomes a "run X pass" suggestion instead.
- **debrief** — deep, file-producing. Reads the retro, proposes a growth-log append.

Include the **rehearsal roleplay** section here (D3): multi-turn interview practice, run
interactively via Claude Code. This is the one BETA-PLAN capability that ships vault-only, and
it works today with no portal involvement.

`tools:` should be read-only (`Read, Grep, Glob`) for a coach that never writes — matching how
[provocateur.md](.claude/agents/provocateur.md) is scoped. If prep/debrief modes need `Write`,
say explicitly in the prompt that sideline mode must not use it.

### 3.2 Five new notes in [10-frameworks/](10-frameworks/)

House format, per [crazy-8s.md](10-frameworks/crazy-8s.md): frontmatter
`type: framework` / `phase` / `status` / `timebox` / `group-size` / `tags` / `created`, then
`## When to use` · `## Steps` · `## Output` · `## Facilitation notes`. Terse — the existing
notes run ~15 lines.

| Note | Phase | Purpose |
|---|---|---|
| `design-sprint-day-by-day.md` | — | Knapp's five-day arc, for orientation |
| `design-sprint-2-agenda.md` | — | 2.0 four-day agenda with timings |
| `time-recovery-playbook.md` | — | what to cut when the room is behind |
| `five-act-interview.md` | decide | the Friday test structure |
| `note-and-vote.md` | converge | quiet decision-making |

Register each in [10-frameworks/index.md](10-frameworks/index.md)'s static list, matching the
existing `[[slug|Label]] — phase · timebox · one-liner` format. The Dataview block picks them up
automatically; the static list does not.

**Wording note, required in each of the sprint-specific notes:** these support the Design Sprint
methodology; no affiliation with GV or AJ&Smart is implied.

The framework library is useful to any facilitator reading the vault directly — this phase has
no portal dependency at all.

### 3.3 What *not* to add

Coach is an **agent**, not a slash command. Do not create `.claude/commands/coach.md` or a
`.cursor/commands/` stub for it. `.cursor/` mirrors commands only, and there is no
`.cursor/agents/` directory.

## Phase 4 — Facilitator growth log

*Depends on Phase 3.*

Create [90-meta/facilitator-growth-log.md](90-meta/facilitator-growth-log.md) per D1, with
`type: meta` frontmatter to satisfy the note contract (`meta` is already an allowed type and is
exempt from the `session:` requirement).

The entry format is the whole deliverable here, and it has one hard requirement: **appending
must be idempotent.** The debrief pass re-reads this file every run for cross-session
aggregation, so a re-run on the same retro must not produce a duplicate entry. Give each entry
a stable, derivable key — the session slug — as a heading:

```markdown
## 2026-07-30-strategy-clinic
```

so a re-run can detect its own prior entry rather than blindly appending. Document that rule in
the file's own header, since the agent reads the file it is about to append to.

Seed it with the one existing session, [30-sessions/2026-07-30-strategy-clinic/60-retro.md](30-sessions/2026-07-30-strategy-clinic/60-retro.md),
written by hand — that both proves the format and gives the debrief pass a worked example to
imitate.

---

## Mirror obligations

Per D7 this repo is canonical for prompts. **Verified baseline: as of this plan, all 6
`.claude/agents/*.md` and all 9 `.claude/commands/*.md` are byte-identical between this repo and
`Ideation-Lab-Web`.** That is the state the portal's drift test locks in — do not break it
casually.

When you change a file in the left column, copy it to the right in the same commit:

| Changed here | Must be mirrored to |
|---|---|
| `.claude/agents/*.md` | `Ideation-Lab-Web/.claude/agents/*.md` |
| `.claude/commands/*.md` | `Ideation-Lab-Web/.claude/commands/*.md` |
| `90-meta/taxonomy.md` | `Ideation-Lab-Web/lib/vault/lint.ts` **and** `Ideation-Lab-Web/docs/vault-contract.md` |

Not mirrored — vault-only: `10-frameworks/`, `90-meta/templates/`, `20-scenarios/`,
`30-sessions/`, `CLAUDE.md`.

**Why this matters more than it looks.** The portal loads prompts from the local filesystem,
trying `process.cwd()/..` first and falling back to its own `.claude/`. On Vercel only its own
copy exists. **A `coach.md` authored here and never mirrored would work perfectly in Claude Code
and never run in production.** The portal's Phase 0 adds a test that fails on drift; until that
test lands, this table is the only thing preventing it.

`.cursor/commands/*.md` are deliberate three-line pointer stubs that delegate to
`.claude/commands/`. They do not need updating when a command's body changes — only when a
command is added or removed.

---

## Sequencing

```text
vault P0 (taxonomy + CLAUDE.md §5.2 + templates)
   └─→ web P0 (lint + contract doc + drift test)
          ├─→ web P1 (stages)                     ─┐
          └─→ vault P3 (coach.md + frameworks)     │  parallel
                 └─→ web P3 (CoachRail)           ─┘
   vault P2 (synthesizer prompt) ─→ web P2 ─→ web P4 + vault P4
```

Vault Phase 0 is the true root of the whole beta. Vault Phases 2 and 3 are independent of each
other and of the portal.

---

## Verification

All of these run in Claude Code against this repo, with no server:

**Phase 0**
- `/weave --check` passes on the whole vault after the taxonomy edit — no existing note is
  invalidated by the four additions.
- Every new field in the templates appears in `CLAUDE.md` §5.2's table. Read both side by side;
  this is the step most likely to be skipped.
- The clean 0.3 samples validate; the deliberately broken ones do not. Hand these to the
  portal's Phase 0 as validator fixtures.

**Phase 2**
- Run `/synthesize` on [30-sessions/2026-07-30-strategy-clinic/](30-sessions/2026-07-30-strategy-clinic/).
  It has 21 real idea notes and an existing `40-synthesis.md` for before/after comparison.
- With no `test-scenario` notes present the pass must still succeed — the session predates them,
  and a prompt that hard-requires verdicts would break every existing session.
- Add two hand-written `test-scenario` notes, re-run, and confirm each gets a verdict with a
  cited evidence link.

**Phase 3**
- `/weave --check` passes on the five new framework notes; each resolves from
  [10-frameworks/index.md](10-frameworks/index.md).
- Invoke coach in sideline mode and confirm the contract holds: one move, one script line, a
  named framework citation, and **no attempt to write a file**. Ask it for something
  write-shaped ("add this to the agenda") and confirm it converts to a "run X pass" suggestion.
- Run one rehearsal roleplay turn (D3) — this is the deliverable that must work here and only
  here.

**Phase 4**
- Append a second entry by hand, then confirm re-appending the *same* session slug is detectable
  as a duplicate by the rule documented in the file header.

**Deferred to its own cycle:** Phase 5 — `20-scenarios/design-sprint-2/` (scenario hub, four-day
agenda seed, prompt pack, capture templates for HMWs / lightning demos / dot-vote outcomes /
test-interview notes, canonical prep checklist) and the beta exit checklist.

**Phase 5 plan draft:** `.claude/plans/jiggly-inventing-sketch.md` — vault-scoped Phase 5 plan,
drafted once 0–4 above were verified. Not yet approved/executed; read it when Phase 5 starts.
