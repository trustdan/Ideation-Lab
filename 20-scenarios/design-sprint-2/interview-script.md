---
type: meta
created: "2026-08-01"
scenario: "[[design-sprint-2]]"
---
# Interview script — design sprint 2.0

<!-- Coach prep-mode output, referenced from agenda-seed.md's Day 3 prep step and run on
Day 4. Extends [[five-act-interview]]'s five acts with this pack's Day 4 specifics — it does
not restate that framework's method. Read [[five-act-interview]] for what each act is *for*;
this fills in what to actually do and say for a design-sprint façade test against the three
sprint questions in the design-sprint-2 hub. -->

## Before each interview
- Confirm which prototype path this interviewee will walk. The prototype must be able to show:
  (a) the onboarding landing screen for Act 3 / ts-01, (b) the first-project creation path
  without the integration-setup gate for Act 4 / ts-02, and (c) the guided-vs-blank-workspace
  choice screen for Act 4 / ts-03.
- Have all three sprint questions and their matching test-scenario notes (`ts-01`, `ts-02`,
  `ts-03`) in front of you. Every interview should move at least one verdict from `pending`.
- One interviewer, one note-taker minimum, per [[five-act-interview]]'s facilitation note;
  the rest of the team watches live where the room allows.
- Capture using `capture-templates.md`'s Test-interview line format:
  `Interview <#>/5, Act <1-5>: <quote/behavior> — <flag: confirms/contradicts ts-0X>`.

---

## Act 1 — Friendly welcome
Per [[five-act-interview]]: put them at ease, no leading framing.

> *"Thanks for making time today — there's no right or wrong answer here. We're testing a
> design, not you, so the more blunt you can be, the more useful this is for us. Before we
> start: any questions about how this works?"*

Do not describe what the product does. Do not use the product name in a way that primes their
Act 3 reaction.

---

## Act 2 — Context questions
Per [[five-act-interview]]: their world and habits, before showing anything.

Lead with the prompt-pack's warm-up question to establish their baseline — this is what Act 4
think-aloud gets compared against:

> *"Before I show you anything: describe the last time you personally worked around a product
> instead of using it as intended — what did you actually do?"*

Then follow up with what the screener surfaced (Q1–Q3 answers are already logged). Useful
probes if the conversation needs it:
- *"When you signed up for [that tool you mentioned], what did you expect to happen in the
  first few minutes?"*
- *"At what point did you feel like you actually 'got it' — or did you?"*

Do not rush Act 2 under time pressure. The baseline it sets is what makes Act 4 silence and
hesitation legible as signal rather than noise.

---

## Act 3 — Introduce the prototype
Per [[five-act-interview]]: frame it as unfinished, ask what they see before explaining anything.

> *"This is very early — think of it as a rough sketch, not a finished product. Before I say
> anything else: what do you think this is?"*

Let them answer fully before following up. This act is where evidence for **ts-01** (unaided
value-prop comprehension within 10 seconds) is generated — resist the urge to explain or
confirm. Note-taker: log the verbatim first description and timestamp.

If they go quiet: *"Just say what's coming to mind — there's no right answer."*
Do not say what the product is, does, or is for until Act 4.

---

## Act 4 — Detailed tasks
Per [[five-act-interview]]: a scenario, think-aloud throughout. One task per sprint question,
mapped to its test-scenario note. Give the scenario, not the mechanic. Let silence sit.

### Task A — maps to ts-02
*(First-project creation without hitting the integration-setup gate)*

> *"Say you've just decided to give this a real try. You want to set up your first project —
> something you'd actually use this week. Show me what you'd do, talking through your thinking
> as you go."*

Note-taker: flag any moment the interviewee pauses at, skips, or backs away from a step.
Specifically watch for: do they encounter the integration-setup screen? Do they abandon,
workaround, or push through?

### Task B — maps to ts-03
*(Guided setup vs. blank workspace choice)*

Only present this task if the prototype reaches the choice screen. If Task A already surfaces
it naturally, do not re-prompt — just observe and flag it.

> *"You've just landed here. What would you do next?"*

Do not describe the two options. Observe which one they move toward and when (immediately vs.
after hesitation). Note-taker: log the choice and any verbalized reasoning.

---

## Act 5 — Quick debrief
Per [[five-act-interview]]: rapid-fire reactions, thank them.

> *"Last few questions — quick reactions, no wrong answers."*
- *"What was the moment you felt most confused?"*
- *"What was the moment, if any, where you felt like you understood what this was for?"*
- *"If you could change one thing about what you just saw, what would it be?"*

Thank them. Don't debrief the sprint questions with them — that framing primes them to
rationalize rather than recall, and the next interviewee may still be waiting.

---

## After all five interviews
Roll the five interviews' captures up against each sprint question during the Day 4 live
synthesis block (agenda-seed.md, Day 4 step 2): tally confirms/contradicts per ts-01, ts-02,
ts-03, and resolve each `verdict` with cited `evidence:` links — per `90-meta/taxonomy.md`'s
rule that any verdict other than `pending` needs at least one evidence link.
