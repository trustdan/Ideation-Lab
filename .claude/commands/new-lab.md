---
description: Create a new session folder from a scenario + the session template
argument-hint: <scenario-slug> <YYYY-MM-DD> <session-slug>
---

Create a new session instance. Arguments: `$ARGUMENTS` (scenario slug, date, session slug).
Governed by CLAUDE.md §5 (note contract) and §11 (scenario contract).

## Procedure

1. **Validate.** Parse the three args. If the scenario folder `20-scenarios/<scenario-slug>/`
   doesn't exist, list available scenarios (Glob `20-scenarios/*/`) and stop. If the date
   isn't `YYYY-MM-DD`, or `30-sessions/<date>-<session-slug>/` already exists, stop with a
   clear message.
2. **Instantiate.** Copy `30-sessions/_template/` → `30-sessions/<date>-<session-slug>/`.
   Rename `session-hub.md` → `<date>-<session-slug>.md` (folder-note pattern — the hub name
   must equal the folder name exactly).
3. **Fill placeholders.** In every copied file, replace:
   - `{{session-link}}` → `"[[<date>-<session-slug>]]"`
   - `{{session-path}}` → `30-sessions/<date>-<session-slug>`
   - `{{scenario-link}}` → `"[[<scenario-slug>]]"`
   - `{{date}}` → the date; `{{created}}` → today.
4. **Pull the brief.** Read the scenario hub (`20-scenarios/<scenario-slug>/<scenario-slug>.md`)
   and copy its outcome/audience/envelope content into the hub's **Brief** section, marked
   as "seeded from scenario — edit freely." Leave the constraint fields (duration, headcount,
   room, attribution) as blanks for the human — do not invent them.
5. **Wire the agenda seed.** In the hub's Next Steps, link the scenario's `agenda-seed.md`
   and `prompt-pack.md` (vault-absolute) so the facilitator finds them.
6. **Set hub frontmatter:** `type: session`, `scenario:`, `date:`, `status: planned`,
   `created:`.
7. **Report:** the created path, and next steps in order — (a) human fills constraints in
   the hub, (b) `/distill`-ready capture starts with `/capture`, but first (c) invoke the
   **facilitator** (offer to do it now if constraints are already filled).

Do not create weave blocks. Do not run the facilitator without constraints present.
