---
description: Produce a single portable, shareable summary of a session
argument-hint: "[session-path] [--anonymize]"
---

Export the session. Arguments: `$ARGUMENTS`.

## Procedure

1. Resolve the session (argument, else latest; ask if ambiguous). Note the `--anonymize`
   flag.
2. Assemble ONE markdown file at `<session>/export/<session-slug>-summary.md`, in this
   order, rewritten to stand alone (a reader has no vault):
   - Header: session name, date, scenario, goal (from the hub Brief).
   - The synthesis **Read-me-first**, themes (names + one-liners), gaps, recommendation.
   - Decisions and actions from `50-actions.md` (owner, date).
   - Optional appendix: idea titles grouped by theme — titles only, not bodies.
3. **Transformations (required):**
   - Strip all frontmatter and all weave blocks.
   - Convert every wikilink to plain text (`[[path|Alias]]` → `Alias`). Zero `[[` may
     remain — the file must read cleanly outside Obsidian.
   - With `--anonymize`: remove person names and `@mentions`, replacing role-relevant ones
     with neutral roles ("the facilitator", "owner A"). Per CLAUDE.md guardrail 6, when in
     doubt, strip.
4. This command writes **only** inside `<session>/export/`. It never modifies source notes.
5. Report the path, word count, and — if `--anonymize` was used — how many
   names/mentions were removed. Remind: nothing outside `export/` is assumed shareable.
