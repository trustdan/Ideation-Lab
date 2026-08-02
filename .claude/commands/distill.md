---
description: Turn raw capture into atomic idea notes (delegates to the scribe)
argument-hint: "[session-path] (default: latest open session)"
---

Distill captures into ideas. Argument (optional session path): `$ARGUMENTS`.

## Procedure

1. Resolve the session: the argument if given, else the most recent hub with `status`
   `planned` or `active`. If ambiguous, ask.
2. Delegate to the **scribe** subagent with the resolved session path. The scribe owns the
   entire procedure (segmentation, dedup, attribution policy, distill log) per its spec.
3. Relay the scribe's run report. Then:
   - If new ideas were created, suggest `/weave <session-path>` to wire them into the graph,
     and `/provoke` or `/synthesize` as the natural next move.
   - If the queue was empty, say so plainly — don't invent work.
   - If the scribe flagged out-of-scope files, surface them plainly too — they stay flagged
     on every re-run until the facilitator moves them into `20-capture/`, never absorbed
     automatically.

This command adds no logic of its own beyond session resolution; the scribe spec is
canonical.
