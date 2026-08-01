---
type: meta
created: 2026-07-31
---
# Facilitator growth log

Cross-session aggregation for the **coach** agent's debrief mode (D1). Append-only.

**Idempotency rule — read this before writing:** each entry is keyed by an `##` heading equal
to the session's slug (e.g. `## 2026-07-30-strategy-clinic`). Before appending, search this
file for that exact heading. If it already exists, the debrief for that session has already
run — report it and stop; do not write a second entry, and do not edit the existing one.
Entries are otherwise never rewritten by later runs; a correction gets a note in a later
session's entry, not a silent edit here.

**Entry shape:**

```markdown
## <session-slug>
**Date:** YYYY-MM-DD · **Scenario:** [[scenario-link]] (or "none")
**Kept doing:** — durable practices this session confirmed were worth repeating
**Changed / stopped:** — things this session's retro flagged as not working
**Trying next:** — what the retro proposes attempting in a future session
**Metric:** — the single number the retro chose as its clearest signal
**Applied from prior entries:** — did this session act on an earlier entry's "Trying next"?
Name which one and what happened, or "n/a — first entry" / "no prior entry applicable."
```

Pull these straight from the session's `60-retro.md` (Keep / Change / Try / One metric
sections) — condense, don't restate the whole retro.

---

## 2026-07-30-strategy-clinic
**Date:** 2026-07-30 · **Scenario:** [[defense-contractor-strategy]]
**Kept doing:**
- Running `/provoke` against the whole synthesis *before* anything hit `50-actions.md` — it
  caught a real, cheap, load-bearing gap (the flagship recompete's own timeline) that a live
  in-room premortem breakout missed.
- The bet-brief step, even as an ad-hoc stub, made the three finalists genuinely comparable
  before premortem.

**Changed / stopped:**
- The gallery walk block produced no capture artifact — either drop it from the scenario's
  `agenda-seed.md` next time, or assign a named capture owner to it.
- Two frameworks (`[[bet-brief]]`, `[[commitment-round]]`) were invented ad hoc mid-agenda and
  are still `status: seed` with `Steps: TODO` — a live risk if this scenario runs again before
  they're field-tested and promoted.
- The room's live commitment-round actions got substantively revised *after* the fact by
  `/provoke` — a gap between what people agreed to in the room and what's actually in
  `50-actions.md`.

**Trying next:**
- Run `/provoke` on each bet-brief right after it's written, *before* the decide gate — not
  only on the finished synthesis afterward.
- Assign a *named* owner for any "independent forcing function" action before the session
  closes, never a "(proposed)" placeholder.

**Metric:** 5 — pre-checks `/provoke` inserted before the room's original kill tests could
run, none of which existed in the decide-gate's own commitments.

**Applied from prior entries:** n/a — first entry.
