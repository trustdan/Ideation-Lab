---
type: meta
created: 2026-07-30
---
# Roadmap — repo growth beyond the note workflow

Living ledger of proposals for what this repo could become, maintained by the **architect**
agent (`/imagine`). Grouped by the lifecycle moment each idea serves (`CLAUDE.md` §4).
Superseded ideas keep their entry — `Status:` gets updated, nothing gets deleted.

## Capture

### Capture hotkey daemon
**What:** a tiny background listener bound to a global hotkey that appends a timestamped line
straight into the active session's `20-capture/` file — no editor, no context switch.
**Serves:** capture
**Why code:** a note can't listen for a keypress outside the app that has focus. This needs an
OS-level hook.
**Effort:** weekend project.
**Trade-off:** OS-specific (Windows/Mac/Linux hotkey APIs differ) — pick one platform first.
**Status:** idea

### Voice-to-capture
**What:** local speech-to-text (e.g. whisper.cpp) piped directly into `20-capture/`, so a
facilitator can capture a spoken aside hands-free mid-session.
**Serves:** capture
**Why code:** audio input and transcription aren't things markdown or an agent-in-a-chat-loop
can do; needs a mic stream and a model.
**Effort:** weekend-to-real-investment (depends on model size / accuracy bar).
**Trade-off:** ships a local model (large-ish download) or takes on a cloud STT dependency —
pick one and say so up front.
**Status:** idea

## Distill

### Capture-to-idea pre-splitter
**What:** a small rule-based script (bullet markers, blank-line runs, timestamp boundaries)
that pre-chunks a raw capture file into candidate idea boundaries before the scribe ever reads
it.
**Serves:** distill
**Why code:** boundary-finding on structural cues is pure logic — no model needed, and doing
it in a script instead of a prompt saves tokens on purely mechanical splitting.
**Effort:** prototype-in-an-afternoon.
**Trade-off:** none — additive, and the scribe can ignore its suggestions entirely.
**Status:** idea

## Synthesize

### Static theme-graph visualizer
**What:** a self-contained HTML file (like an Artifact), regenerated deterministically like
`/weave`, rendering a force-directed graph of ideas and themes straight from `theme:` and
`related:` frontmatter — a visual sibling to the weave block, not a replacement.
**Serves:** synthesize
**Why code:** layout and interactive graph rendering is a visual/spatial task a markdown block
can't do; static HTML keeps it plugin-free, matching the weave-block philosophy (§5.3 rule 5).
**Effort:** weekend project.
**Trade-off:** none if hand-rolled (inline JS/canvas, no CDN) — must regenerate idempotently
like `/weave` or it becomes another source of drift.
**Status:** idea

### Dot-voting tally script
**What:** a CLI that reads raw dot-vote counts (captured as a plain text/CSV list during a live
session) and outputs ranked results ready to paste into synthesis.
**Serves:** synthesize
**Why code:** it's arithmetic and sorting — genuinely simpler and more auditable as a script
than as a prompt, and it's instant (no model round-trip) during a live, timeboxed session.
**Effort:** prototype-in-an-afternoon.
**Trade-off:** none — additive, mirrors the existing [[dot-voting]] framework rather than
replacing it.
**Status:** idea

## Provoke

### Provocation card deck (printable)
**What:** generate a printable PDF deck of provocation cards from `prompt-pack.md` +
`90-meta/taxonomy.md` — for in-person premortem/steelman rounds where a laptop breaks the
room's energy.
**Serves:** provoke
**Why code:** PDF layout and print-ready output is not something a markdown note produces on
its own.
**Effort:** weekend project.
**Trade-off:** takes on a PDF-generation dependency (e.g. a lightweight typesetting lib).
**Status:** idea

## Retro / Export

### Static export microsite generator
**What:** a build script that reads a session's frontmatter and renders a small static HTML
site (hub, synthesis, actions) — for stakeholders without Obsidian, complementing (not
replacing) the single-file `/export` summary.
**Serves:** export
**Why code:** multi-page navigable output with real styling is beyond a single markdown file;
static HTML keeps it correct with zero plugins, same guarantee the vault already makes.
**Effort:** weekend project.
**Trade-off:** none if it stays a pure reader of existing frontmatter — must not become a
second source of truth.
**Status:** idea

### Actions → calendar/reminders exporter
**What:** parse `50-actions.md` (owner + date + status, already structured per taxonomy) and
emit `.ics` files, or push to a task tool.
**Serves:** export
**Why code:** calendar file formats and task-tool APIs are outside markdown's job.
**Effort:** prototype-in-an-afternoon.
**Trade-off:** none for `.ics` (plain text format); a task-tool push adds an API dependency —
keep that path optional.
**Status:** idea

## Repo-level

### Weave-graph CLI (dependency-free reimplementation)
**What:** a small compiled binary (Rust/Go) that reimplements what `/weave --check` does —
runnable in a pre-commit hook or CI to catch broken links and stale weave blocks without
invoking Claude at all.
**Serves:** repo-level
**Why code:** deterministic graph validation belongs in a fast, offline binary if it's going to
gate commits — matches "must be correct without plugins" taken to its logical end.
**Effort:** real-investment.
**Trade-off:** the audit logic now lives in two places (the librarian's spec and this binary)
— they will drift unless one is generated from the other, or the binary's rule set is kept
deliberately smaller (mechanical checks only, judgment calls stay with the librarian).
**Status:** idea

### Choose-your-own-adventure scenario-authoring TUI (ratatui)
**What:** a terminal decision tree — no AI, pure logic gates encoded in a small data file
(RON/YAML) shipped alongside the binary — that walks a facilitator through questions
(headcount? goal? time? divergent or convergent bias?) and, at the end, **generates a real
`agenda-seed.md` / `prompt-pack.md`** into a new scenario folder. Not a toy alongside §11's
scenario contract — an alternative front door into it.
**Serves:** repo-level (specifically: scenario authoring, §11)
**Why code:** a branching, stateful Q&A flow with a satisfying terminal UI is something a
static note can't be; ratatui gives you a real interactive experience for the price of a
single binary.
**Effort:** weekend project.
**Trade-off:** adds a Rust toolchain as an *optional* dependency for anyone who wants to build
it — the plain "copy `_template/` and fill it in" path (§11) must keep working unmodified for
forks that never touch Rust.
**Status:** idea

### Web portal with live Claude chat co-pilot
**What:** the same guided decision-tree experience as the TUI, browser-based, with a
chat-with-Claude panel layered in — usable live, projected in the room, where the chat's job
is specifically to widen divergent framing (HMW variants, alternate framings) rather than
replace the facilitator.
**Serves:** repo-level (scenario authoring + live-session facilitation aid)
**Why code:** real-time chat UI and shared-screen interaction during a live session is not a
markdown-note task.
**Effort:** real-investment (hosting, API key handling, chat UI, session state).
**Trade-off:** this is the one idea in this file that breaks "no AI required" — it takes on a
live API dependency and a cost-per-use. Keep it a clearly separate, optional mode from the
logic-only TUI above, not a replacement for it.
**Status:** idea

## Run report

Ideas added: 11 (2 from the user's seed, 9 new). Effort spread: 4 prototype-in-an-afternoon
(pre-splitter, dot-voting tally, actions exporter, and — closely — the card deck's data prep),
5 weekend projects (hotkey daemon, theme-graph visualizer, card deck, export microsite, CYOA
TUI), 2 real-investment (weave-graph CLI, web portal + chat), 1 that spans both bands
(voice-to-capture).

**If you only had a weekend:** the **CYOA scenario-authoring TUI**. It's genuinely
weekend-sized, needs no external API or ongoing cost, and — unlike a standalone toy — plugs
directly into a real seam the repo already has (§11's scenario contract), so what it produces
is immediately useful rather than a demo. The web portal + Claude chat is the more ambitious
sibling idea; worth doing once the TUI proves the decision-tree logic is worth encoding at
all.
