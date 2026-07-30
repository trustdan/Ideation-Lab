---
description: Cluster the idea pool into themes and draft the synthesis (delegates to the synthesizer)
argument-hint: "[session-path] (default: latest open session)"
---

Synthesize the session's ideas. Argument (optional session path): `$ARGUMENTS`.

## Procedure

1. Resolve the session (argument, else latest open hub; ask if ambiguous).
2. **Precondition:** count notes in `<session>/30-ideas/`. If < 6 ideas, stop and report —
   recommend more capture/distill or another divergent block instead of a forced synthesis.
   Also check `_distill-log.md` vs `20-capture/`: if undistilled captures exist, recommend
   `/distill` first (offer to run it) so the synthesis sees the whole pool.
3. Delegate to the **synthesizer** subagent with the session path. It writes
   `40-synthesis.md` and applies `theme:` frontmatter per its spec.
4. Relay the run report. Suggest, in order: `/provoke 40-synthesis.md` (pressure-test the
   recommendation before it hardens), then `/weave <session-path>` (themes just changed the
   relation graph), then moving decisions into `50-actions.md`.
5. If this is a re-run, note in the report which themes changed names or membership since
   the last synthesis (git diff of `40-synthesis.md` if available).
