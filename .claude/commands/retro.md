---
description: Write the session retrospective — plan vs. reality, keep/change/try, action check
argument-hint: "[session-path] (default: latest open session)"
---

Write the retro. Argument (optional session path): `$ARGUMENTS`.

## Procedure

1. Resolve the session (argument, else latest open hub; ask if ambiguous).
2. Gather evidence — this retro is grounded, not vibes:
   - `10-agenda.md`: the plan. For each block, did its named **Output** actually appear
     (captures / ideas / synthesis sections)? Build a small plan-vs-reality table.
   - Counts: captures, ideas, challenges, themes; unclustered ideas.
   - `50-actions.md`: does every `decide`-phase outcome have an owner and a date?
3. Write `<session>/60-retro.md` (`type: retro`, `session:` link):
   - **Plan vs. reality** table (block | planned output | happened? | note).
   - **Keep / Change / Try** — for the *process*, not the ideas. Feed "Try" items back:
     anything reusable becomes a suggested edit to the scenario or a framework note — list
     the concrete edit, don't silently apply it.
   - **Action follow-through** — actions lacking owner/date, flagged.
   - **One metric** — the single number that best tells whether this lab worked, and its
     value today.
4. Set the hub `status: closed` (frontmatter edit) unless open actions argue for
   `synthesized` — say which you chose and why.
5. Report, and suggest `/export` if the summary needs to travel.
