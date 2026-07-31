# CLAUDE.md

**This file is the single authoritative source of truth for this repository.** Every other
instruction surface — `AGENTS.md`, `.cursor/rules/`, `.cursor/commands/` — is a thin adapter
that defers here. If any instruction anywhere conflicts with this file, this file wins.
Conventions change here first, then get mirrored outward.

---

## 1. What this repo is

A dual-surface repository for planning and running **team offsites and innovation / ideation
labs**. The same files serve three tools at once:

- **Obsidian** — the repo root *is* the vault. Open the root folder directly. Dot-directories
  (`.claude/`, `.cursor/`, `.git/`, `.obsidian/` internals) are invisible to the vault.
- **Cursor** — reads `AGENTS.md` and `.cursor/rules/`, both of which point here.
- **Claude Code** — reads this file, plus the agents and commands in `.claude/`.

The **unit of reuse is a Scenario** (`20-scenarios/`): a self-contained payload describing a
kind of lab. The **unit of work is a Session** (`30-sessions/`): a dated instance of running
one. The intended fork workflow: fork the repo → drop in or author a scenario → `/new-lab` →
run the session with the agents → `/export` the results.

## 2. Authority and division of labor

Keep each layer doing its one job. Do not duplicate content across layers.

| Layer | Holds | Loaded |
|---|---|---|
| `CLAUDE.md` (this file) | Contracts, conventions, schemas, guardrails | Always |
| `.claude/commands/*.md` | **Procedures** — step-by-step, one per slash command | On invocation |
| `.claude/agents/*.md` | **Roles** — system prompts for specialized subagents | On delegation |
| `90-meta/taxonomy.md` | **Vocabulary values** — the allowed values for schema fields | Referenced by agents |
| `AGENTS.md`, `.cursor/rules/00-core.mdc` | Pointers to this file. Nothing else. | By Cursor |

Rules that follow from this:

1. **No procedures in CLAUDE.md.** If you're writing numbered steps for how to do something,
   it belongs in a command spec.
2. **No vocabulary values in CLAUDE.md.** This file defines *which fields exist* and what they
   mean; `90-meta/taxonomy.md` defines *which values are allowed*. Forks customize vocabulary
   without touching this file.
3. **Adapters never diverge.** `AGENTS.md` and the Cursor rules must never contain a rule that
   isn't a restatement of "read CLAUDE.md."

**Changing a convention:** (1) edit this file → (2) update `90-meta/taxonomy.md` if vocabulary
changed → (3) update the affected command/agent specs if a procedure changed → (4) run
`/weave --check` to surface anything the change broke.

## 3. Repo map

```
CLAUDE.md                  ← you are here; canonical
AGENTS.md                  ← stub → CLAUDE.md (read natively by Cursor)
README.md                  ← fork-and-go quickstart
.claude/agents/            ← facilitator, scribe, synthesizer, provocateur, librarian
.claude/commands/          ← new-lab, capture, distill, synthesize, provoke, weave, retro, export
.cursor/rules/             ← 00-core (alwaysApply pointer), 10-vault (note-contract enforcement)
.cursor/commands/          ← thin mirrors; each executes the matching .claude/commands spec
.obsidian/                 ← minimal committed config; workspace.json is gitignored
00-start-here/             ← orientation + fork checklist
10-frameworks/             ← evergreen method library (Crazy 8s, HMW, dot voting, premortem, …)
20-scenarios/              ← drop-in use-case payloads; _template/ defines the shape
30-sessions/               ← dated working folders, one per real event; _template/ defines the shape
90-meta/                   ← taxonomy.md, linking-spec.md, roadmap.md, templates/, attachments/
```

## 4. Domain model and lifecycle

| Concept | Definition | Lives in |
|---|---|---|
| **Framework** | A reusable facilitation method (timebox, steps, output) | `10-frameworks/` |
| **Scenario** | A reusable lab definition: brief, constraints, agenda seed, prompt pack | `20-scenarios/<slug>/` |
| **Session** | One dated run of a scenario with a real team | `30-sessions/<YYYY-MM-DD-slug>/` |
| **Capture** | Raw, unedited notes taken during a session | `<session>/20-capture/` |
| **Idea** | One atomic idea distilled from capture — one idea per file | `<session>/30-ideas/` |
| **Challenge** | A red-team note targeting an idea, theme, or synthesis | `<session>/30-ideas/challenge-*.md` |
| **Synthesis** | Clustered themes, tensions, gaps, and a recommendation | `<session>/40-synthesis.md` |
| **Actions** | Committed next steps with owners and dates | `<session>/50-actions.md` |
| **Retro** | What happened vs. plan; keep / change / try | `<session>/60-retro.md` |

**Lifecycle:** Scenario → `/new-lab` → Session → `/capture` (during) → `/distill` → ideas →
`/provoke` (optional) → `/synthesize` → decisions → `50-actions.md` → `/retro` → `/export`.

**Phases** describe where a note sits in the thinking arc: `diverge → converge → decide →
commit`. Agendas should follow that arc; ideas are born in `diverge`.

## 5. The note contract

Every markdown note in the content directories (`00-`, `10-`, `20-`, `30-`, `90-meta/` except
`templates/`) follows this contract. Paths matching `_template/` or `90-meta/templates/` are
**exempt** and are ignored by validation.

### 5.1 Filenames and folders

- All filenames and folders: **kebab-case**, `.md` extension, no spaces.
- Session folders: `YYYY-MM-DD-slug` (e.g. `2026-08-12-product-offsite`).
- **Session hub note = folder-note pattern.** Every session folder contains exactly one note
  named identically to the folder (`2026-08-12-product-offsite.md`). This is the session's
  hub and its *only* stable link target: `[[2026-08-12-product-offsite]]`. It holds the brief
  and links out to everything else. Because the filename embeds the date and slug, hub links
  are globally unique in the vault.
- Working files inside a session keep fixed numbered names (`10-agenda.md`, `40-synthesis.md`,
  …). These names repeat across sessions, so they are **ambiguous link targets** — see §6.
- Idea filenames are descriptive slugs of the idea itself (`usage-based-pricing-riff.md`), not
  numbers. The librarian flags cross-session duplicate idea filenames.

### 5.2 Frontmatter (start matter)

YAML frontmatter is the machine-readable truth about a note. Schema — allowed *values* for
each field live in `90-meta/taxonomy.md`:

| Field | Type | Required on | Meaning |
|---|---|---|---|
| `type` | string | **every note** | What kind of note this is |
| `session` | wikilink | every note inside a session folder *except the hub* | The owning session's hub |
| `scenario` | wikilink | session hubs; prep-checklists and follow-throughs (pack-level, no owning session) | The scenario this session or pack artifact instantiates |
| `date` | YYYY-MM-DD | session hubs, captures | Event / capture date |
| `status` | string | session hubs, ideas, actions, prep-checklists, follow-throughs | Lifecycle state (per-type vocab in taxonomy) |
| `phase` | string | ideas, challenges | Where in diverge→commit this belongs |
| `theme` | string | ideas (set by synthesizer) | Cluster name assigned during synthesis |
| `frameworks` | list of wikilinks | optional | Provenance: which method(s) produced this |
| `related` | list of wikilinks | optional | Curated associations; primary input to `/weave` |
| `distilled-from` | wikilink (path-qualified) | ideas | The capture file this came from |
| `targets` | list of wikilinks | challenges | What this challenge attacks |
| `tags` | list | optional | Lowercase-kebab topical tags |
| `created` | YYYY-MM-DD | every note | Creation date |
| `method` | string | decisions | How the call was made (vocab in taxonomy: decision methods) |
| `decider` | string | decisions | Who (by role) made or ratified the call |
| `options` | list of wikilinks | decisions | The alternatives that were on the table |
| `outcome` | string | decisions | The option chosen, in one line |
| `rationale` | string | decisions | Why, in one line |
| `made-during` | wikilink | decisions | The agenda block or session moment the call happened in |
| `id` | string | test-scenarios | Stable identifier a scenario hub can link back to |
| `sprint-question` | string | test-scenarios | The sprint question this scenario is testing |
| `verdict` | string | test-scenarios | Result (vocab in taxonomy: test-scenario verdicts); default `pending` |
| `evidence` | list of wikilinks | test-scenarios | Notes supporting a non-`pending` verdict |

Frontmatter rules:

- Wikilink values are quoted strings: `session: "[[2026-08-12-product-offsite]]"`. Obsidian
  treats link-valued properties as real links (backlinks + graph) with no plugins.
- Humans and agents may edit frontmatter freely, **except** `theme` (synthesizer owns it) and
  fields inside `_distill-log.md` (scribe owns it).
- Unknown extra fields are allowed (forks may extend); the librarian warns but doesn't fail.

### 5.3 End matter (the weave block)

Each note *may* end with exactly one generated block, delimited by HTML-comment markers:

```markdown
<!-- weave:start -->
## Related
- [[30-sessions/2026-08-12-product-offsite/30-ideas/tiered-pricing|Tiered pricing]] — same theme: pricing-models
- [[crazy-8s|Crazy 8s]] — shared framework
<!-- weave:end -->
```

Hard rules:

1. **Only `/weave` writes inside the markers.** Humans and every other agent treat the
   interior as read-only. To influence it, edit `related:` frontmatter and re-run `/weave`.
2. The block is **fully regenerated** on every run — never patched. Running `/weave` twice in
   a row must produce zero diff (idempotency is a correctness requirement).
3. Notes with no relations get **no block at all**; a block that becomes empty is removed.
   This keeps diffs clean and empty notes uncluttered.
4. The block sits at the very end of the file, preceded by one blank line.
5. Because the block is static markdown, links render everywhere — GitHub, Cursor preview,
   and Obsidian with zero plugins. Dataview and other live-query plugins are *enhancements*
   layered on top; **nothing in this repo may depend on a plugin to be correct**.

### 5.4 Editing rights

| Region | Humans | Facilitator / Scribe / Synthesizer / Provocateur | Librarian (`/weave`) |
|---|---|---|---|
| Body prose | ✅ | ✅ in their output files only | ❌ never |
| Frontmatter | ✅ | ✅ per §5.2 ownership | ✅ audit fixes only, reported |
| Weave block interior | ❌ | ❌ | ✅ sole writer |
| `20-capture/` raw files | ✅ append | ❌ read-only (state lives in `_distill-log.md`) | ❌ |

### 5.5 Atomicity

One idea per file. If a capture chunk contains three ideas, it becomes three files. If two
files describe the same idea, they become one file plus a `related` link from anything that
referenced the duplicate. Atomic notes are what make the graph, the weave, and synthesis
clustering actually work.

## 6. Linking rules

1. **Wikilinks everywhere** (`[[target]]` / `[[target|Alias]]`), never bare markdown URLs for
   internal links. The committed Obsidian config sets link format to vault-absolute paths and
   auto-updates links on rename.
2. **Generated links are vault-absolute with an alias**:
   `[[30-sessions/2026-08-12-x/40-synthesis|Synthesis]]`. Generated = anything written by an
   agent or command. This makes links unambiguous even though working filenames repeat across
   sessions.
3. **Human links may be lazy** (`[[crazy-8s]]`) when the target filename is unique. Linking to
   another session's internals requires the path-qualified form; linking to the session itself
   uses the hub (`[[2026-08-12-product-offsite]]`), which is always unique.
4. **Where associations go:** provenance → `frameworks:`; attack relationships → `targets:`;
   everything else deliberate → `related:`; loose topical grouping → `tags:`. Prose links are
   fine but only frontmatter feeds `/weave` deterministically.
5. `/weave` derives relations from, in order: explicit `related:`, `targets:`,
   `distilled-from:`, shared `theme` within a session, shared `frameworks`. It never guesses
   from prose similarity — the weave must be explainable from frontmatter alone.

## 7. Agents

Specs live in `.claude/agents/`. Summary of who does what:

| Agent | One-liner | Writes to |
|---|---|---|
| **facilitator** | Composes a timeboxed agenda from the framework library given the session brief | `<session>/10-agenda.md` |
| **scribe** | Distills raw capture into atomic idea notes with valid frontmatter | `<session>/30-ideas/`, `_distill-log.md` |
| **synthesizer** | Clusters ideas into named themes; writes tensions, gaps, recommendation | `<session>/40-synthesis.md`, `theme:` on ideas |
| **provocateur** | Red-teams ideas/synthesis: assumptions, kill tests, premortem, steelman | `<session>/30-ideas/challenge-*.md` |
| **librarian** | Audits the note contract; runs the weave | Weave blocks; frontmatter fixes |
| **architect** | Envisions repo-level growth beyond the note workflow — new tools, surfaces, integrations, including non-markdown code | `90-meta/roadmap.md` |

The architect is the one exception to "operates on session content": it proposes, it doesn't
implement without being asked, and its output (`90-meta/roadmap.md`) is `type: meta`, exempt
from the session-note schema in §5.2. It still answers to the guardrails in §12.

Shared rules for **all** agents:

- Validate every field you write against `90-meta/taxonomy.md` before writing.
- Write only inside your designated output paths (table above). Never delete a note — set
  `status: parked` instead.
- Prefer linking to duplicating. Search (`Grep`/`Glob`) for existing notes before creating.
- End every run with a short **run report**: files created/modified, counts, and any contract
  violations you noticed but didn't fix.
- Ideas are unattributed by default. Do not name who said what in distilled notes unless the
  session hub sets `attribution: open`. Psychological safety is a default, not an option.

## 8. Commands

Canonical procedures live in `.claude/commands/`. Cursor mirrors in `.cursor/commands/` do
nothing but execute the canonical spec.

| Command | Args | Delegates to | Produces |
|---|---|---|---|
| `/new-lab` | `<scenario-slug> <YYYY-MM-DD> <session-slug>` | — | New session folder from templates, prefilled |
| `/capture` | freeform text (or file path) | — | Timestamped raw note in `20-capture/` |
| `/distill` | `[session-path]` (default: latest open) | scribe | Atomic ideas + distill log |
| `/synthesize` | `[session-path]` | synthesizer | `40-synthesis.md`, themed ideas |
| `/provoke` | `<target-path or theme>` | provocateur | Challenge note(s) |
| `/weave` | `[scope-path] \| --all \| --check` | librarian | Regenerated weave blocks + report |
| `/retro` | `[session-path]` | — | `60-retro.md` |
| `/export` | `[session-path] [--anonymize]` | — | Single portable summary in `<session>/export/` |
| `/imagine` | `[topic or constraint]` | architect | Proposals appended/updated in `90-meta/roadmap.md` |

## 9. Obsidian specifics

- Open the **repo root** as the vault. Never nest a vault in a subfolder.
- `.obsidian/` is committed minimally (link settings, plugin list); `workspace.json` is
  gitignored so forks don't inherit open tabs.
- Recommended community plugin: **Dataview** — used for live dashboards (e.g. the frameworks
  index). Per §5.3, Dataview output is always accompanied by, or degradable to, static
  content. If a note must be correct without plugins, it is.

## 10. Cursor / Claude Code specifics

- Cursor: `AGENTS.md` and `.cursor/rules/00-core.mdc` route you here; `10-vault.mdc` attaches
  the note contract to any markdown file you touch.
- Claude Code: subagents auto-delegate based on the `description` field in each agent spec;
  invoke commands as slash commands. When acting without a command, you are still bound by
  §5–§6 and the guardrails below.
- `.claude/settings.json` allowlists only read-only operations (`Read`, `Glob`, `Grep`, and
  `git status`/`diff`/`log`) by default. Writes, other Bash commands, and anything not listed
  will prompt the human for approval — expected, not a bug.

## 11. Authoring a scenario (the platform contract)

A scenario is a folder in `20-scenarios/<slug>/`, self-contained, all links relative or
vault-absolute. Copy `20-scenarios/_template/`. Required files:

- `<slug>.md` — scenario hub (folder-note pattern, same as sessions). `type: scenario`.
  States: who this lab is for, the outcome it produces, headcount/duration envelope.
- `agenda-seed.md` — ordered list of framework links + rough timeboxes the facilitator uses
  as a starting bias (not a mandate).
- `prompt-pack.md` — seed questions, HMW stems, and provocations specific to the use case.
- `references.md` — optional background links/docs participants should see.

`/new-lab` consumes the scenario by: copying the session template, linking the hub to the
scenario, pulling the scenario brief into the session hub, and handing `agenda-seed.md` to the
facilitator. A fork that only ever adds scenario folders never needs to touch anything else.

## 12. Guardrails (always-rules)

1. Never edit between `weave:start` and `weave:end` unless you are `/weave`.
2. Never modify raw capture files after creation. Capture is an append-only inbox; distill
   state lives in `_distill-log.md`.
3. Never delete or overwrite human prose. Park, link, or append.
4. Never rename a note without fixing every inbound link in the same change (the librarian
   can do this; Obsidian does it automatically in-app).
5. Never attribute ideas to named people in generated notes unless the hub opts in (§7).
6. Session content may contain sensitive team information. `/export --anonymize` must strip
   names and `@mentions`; nothing outside `export/` is ever assumed shareable.
7. Templates (`_template/`, `90-meta/templates/`) are exempt from validation and must keep
   their `{{placeholder}}` tokens — don't "fix" them.

## 13. Git conventions

- Commit at command boundaries. Message format: `[<session-slug>|meta] <command-or-verb>: summary`
  — e.g. `[2026-08-12-product-offsite] distill: 14 ideas from 3 captures`.
- Generated churn (weave blocks) should be its own commit (`weave:`) so content diffs stay
  readable.
- Forks: see `00-start-here/fork-checklist.md`.
