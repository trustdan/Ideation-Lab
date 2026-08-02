---
description: Draft or advance a phased plan.md checklist from a facilitator-confirmed brief
argument-hint: "[session-path] (default: latest open session)"
---

Write or advance the plan. Argument (optional session path): `$ARGUMENTS`.

## Procedure

1. Resolve the session (argument, else latest open hub; ask if ambiguous).
2. Check whether `<session>/00-meta/plan.md` already exists.

### No existing plan

1. Gather context — a plan should fit the session it lives in, not float free of it:
   - `10-agenda.md` and `50-actions.md`: what's already scheduled or owed.
   - `40-synthesis.md`: themes and recommendations already on the table.
   - The confirmed brief: the settled scope from the facilitator's clarifying-question round.
     Treat it as final — don't reopen questions the facilitator already answered.
2. Write `<session>/00-meta/plan.md` (`type: plan`, `session:` link, `status: draft`):
   - One `## Phase N: <title>` section per anticipated phase.
   - Flesh out **only Phase 1** with a real `- [ ] task` checklist (roughly 6-10 items —
     small enough that a facilitator or assistant can execute and close it out inside a
     single chat thread; this app hard-caps a thread at 30 messages).
   - Every later phase is a one-line stub (e.g. `_Not started yet._`) with no checklist
     items yet. Don't lock in scope for work nobody's reached — that's the whole point of
     phasing this instead of writing one giant plan up front.

### An existing plan

1. Read it. Identify the next stub phase (or, if every phase is already checked off and
   the brief describes further work, the phase one number higher than the last one shown).
2. Draft **only that one phase** — its heading, a one-line `Resume:` note (what to check or
   re-read before starting fresh with no memory of earlier phases), and its checklist.
   Never touch, reproduce, or re-derive any other phase — the runner splices your one phase
   into the existing file deterministically, which is what keeps already-checked-off items
   and earlier phases safe from being silently rewritten.

## Report

Name the phase count so far and which phase just got drafted, and note that the file is
ready to review and publish — a fresh chat thread reads the plan back automatically and
picks up from the current phase without needing to be re-briefed.
