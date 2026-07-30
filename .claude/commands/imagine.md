---
description: Brainstorm repo-level growth beyond the note workflow (delegates to the architect)
argument-hint: "[topic or constraint, e.g. \"non-markdown tooling\"]"
---

Run a repo-growth brainstorm. Arguments (optional direction/constraint): `$ARGUMENTS`.

## Procedure

1. Delegate to the **architect** subagent, passing along any topic/constraint given. Its spec
   is canonical for stance, scope, and the `90-meta/roadmap.md` entry shape — add nothing.
2. The architect proposes; it does not implement. If its output makes you want to actually
   build something, that's a separate, explicit ask from the user — don't skip ahead.
3. Relay the run report, then surface the "if you only had a weekend" pick first — that's the
   highest-signal line for deciding what to do next.

Reminder (`CLAUDE.md` §12): the architect never writes inside weave markers, never touches
session content, and never deletes a roadmap entry — superseded ideas get their `Status:`
line updated in place, not removed.
