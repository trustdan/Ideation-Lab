---
description: Red-team an idea, theme, or the synthesis (delegates to the provocateur)
argument-hint: <target: idea path | theme name | 40-synthesis.md> [session-path]
---

Challenge a target: `$ARGUMENTS`.

## Procedure

1. Resolve the session (explicit path in args, else latest open hub).
2. Resolve the target:
   - A path → that note.
   - A theme name → all ideas in the session whose `theme:` matches (the theme is the
     target; the provocateur picks its strongest member to attack concretely).
   - `synthesis` / `40-synthesis.md` → the synthesis note.
   - No target given → default to the synthesis if it exists, else ask.
3. Delegate to the **provocateur** subagent (target + session). It writes
   `challenge-*.md` notes per its spec — max three per run.
4. Relay the run report, leading with the verdicts. Suggest `/weave <session-path>` so
   `targets:` back-references appear on the challenged notes, and — if any verdict was
   `reshape` — a scribe pass to spawn the reframes as new seed ideas.
