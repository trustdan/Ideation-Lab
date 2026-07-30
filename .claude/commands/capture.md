---
description: Append a raw, timestamped capture note to the active session (zero cleanup by design)
argument-hint: <freeform text, or a file path to ingest>
---

Capture raw material: `$ARGUMENTS`. Speed over polish — this is an inbox, not a document.

## Procedure

1. **Resolve session.** Target the most recent session whose hub `status` is `planned` or
   `active` (Glob `30-sessions/*/`, read hubs). If none, or if several are `active`, ask
   which session — never guess between live sessions.
2. **Write the note** at `<session>/20-capture/<YYYY-MM-DD-HHMM>-<two-word-slug>.md`:
   - Frontmatter only: `type: capture`, `session:` (hub link), `date:`, `created:`.
   - Body: the argument text **verbatim** — no rewording, no formatting fixes, no
     summarizing. If the argument is a file path, copy that file's content in verbatim and
     note the origin path on the first line.
3. If the hub `status` is still `planned`, set it to `active` (frontmatter edit, report it).
4. **Report** the path, and a running count of undistilled captures (files in `20-capture/`
   minus entries in `_distill-log.md`). If ≥3, suggest `/distill`.

Guardrails: never edit existing capture files (CLAUDE.md guardrail 2); one capture call =
one new file.
