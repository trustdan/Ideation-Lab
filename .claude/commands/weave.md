---
description: Regenerate end-matter Related blocks from frontmatter, or audit the note contract (delegates to the librarian)
argument-hint: "[scope-path] | --all | --check [--fix]"
---

Run the weave / audit. Arguments: `$ARGUMENTS`.

## Procedure

1. Parse the mode:
   - `--check` → librarian **AUDIT** mode (add `--fix` to also apply mechanical fixes).
   - a path → librarian **WEAVE** scoped to that path (typically one session folder).
   - `--all` or no args → confirm intent if the vault is large, then **WEAVE** over all
     content dirs.
2. Delegate to the **librarian** subagent with the mode and scope. Its spec is canonical
   for relation derivation, rendering, ordering, and the idempotency check — add nothing.
3. Relay the run report. If WEAVE touched files, recommend committing them as a standalone
   commit: `weave: <n> files, +<a>/-<r> links` (CLAUDE.md §13 — generated churn stays out
   of content diffs).
4. If the librarian reported an idempotency failure or hand-edits inside weave markers,
   surface that **first** — it means the contract is being violated somewhere and weaving
   again will not fix it.

Reminder (CLAUDE.md guardrail 1): nothing but this command's librarian run ever writes
between weave markers.
