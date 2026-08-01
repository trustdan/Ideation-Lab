---
type: prep-checklist
scenario: "[[design-sprint-2]]"
status: drafting
created: "2026-08-01"
---
# Prep checklist: Design sprint 2.0

<!-- This pack ships as a reusable scenario type, not a single real engagement (see the hub's
Long-term-goal / Sprint-questions sections). This checklist is written the same way: concrete
guidance for whoever runs a real sprint from this pack, not fabricated specifics for a client
that doesn't exist. Fill in the bracketed specifics once a real sprint question and target
user are set, then move status to `ready` only once every gating item below is actually
confirmed — not merely drafted. -->

## Recruit
- **Target profile:** New or prospective self-serve SaaS users — people who have signed up for
  a product on their own (without a sales touch) in the last 90 days, or who regularly evaluate
  and adopt SaaS tools independently. They must have personally experienced onboarding friction
  or drop-off; power users, internal employees, and consultants who've seen every competitor
  should be screened out unless that profile is explicitly the target.
- **Core team, Days 1–3:** 5–7 people plus the decider (the decider can be one of the 5–7 or a
  separate stakeholder who joins for the Day 2 supervote and Day 4 synthesis — see Decider below).
- **External test interviewees, Day 4:** 5, matching the self-serve signup profile above — not a
  coworker or friend of convenience. Five is the Design Sprint / usability convention: enough to
  surface dominant patterns without drowning Day 4's live synthesis in more transcript than can be
  reviewed same-day.
- **Best-fit profile:** People who have recently gone through a SaaS self-serve onboarding flow
  and either completed it, abandoned it, or built a workaround (e.g. skipped setup, went straight
  to docs, called support). Ideally they can recall a specific recent instance — the screener
  questions below are designed to surface this. Someone who has never self-serve-signed-up for
  anything cannot validate the sprint questions about unaided comprehension or first-task
  completion.
- **Lead time:** External recruiting for Day 4 typically needs 1–2 weeks. Start it in parallel
  with Day 1 planning, not after Day 2 — the screener questions below can be drafted before the
  winning direction is chosen.
- **Backups:** Line up 1–2 alternates for Day 4 no-shows. Five clean interviews beats five
  merely-scheduled ones.

## Decider
- Name the specific person, by role, who can make the Day 2 supervote call and rule on the
  Day 4 synthesis. "Available all week" is not confirmation — get explicit calendar blocking for
  those two specific moments, in writing, before Day 1. This is the hub's Known failure mode #1
  and the exact gap this section exists to catch.
- If the real decider genuinely cannot attend one of those moments, name their delegate in
  advance, with the same authority, rather than discovering the gap live.
- The decider needs to be *in the room* for the supervote, not briefed afterward — the method's
  whole premise (Knapp, *Sprint*) is a single accountable person cutting design-by-committee
  debate short, live.
- **[Confirm and fill in before Day 1]:** _______________________ (name / role), confirmed
  available for Day 2 supervote and Day 4 synthesis.

## Room & supplies
- One room the team holds for all 4 consecutive days without being displaced — storyboards,
  the target map, and dot-vote sheets need to stay on the walls overnight between days.
- Wall/whiteboard space for: expert-interview notes and the target map (Day 1); a storyboard
  gallery large enough for a silent heat-map critique and dot voting (Day 2).
- Supplies: sticky notes, dot stickers (or markers as a substitute) for voting, sharpies,
  large paper or whiteboard surface for storyboards, a visible timer.
- Day 3 façade build: a no-code prototyping tool suited to the onboarding flow being tested
  (Figma, Keynote, or a clickable mockup). The prototype must be able to show at minimum:
  (a) the first 10 seconds of the onboarding landing screen (for ts-01), (b) the first-project
  creation path without the integration-setup gate (for ts-02), and (c) a branching choice
  screen showing both guided setup and blank workspace (for ts-03).
- Day 4: a separate, quieter space for one-on-one interviews, plus a way for the rest of the
  team to watch live (side-room video feed, one-way setup, or quiet observer seats if the
  interviewee is comfortable). Per [[five-act-interview]], team reactions during the interview
  are as valuable as the transcript.
- **[Confirm room booking before Day 1]:** room name/location _______________________, booked
  Days 1–4, walls available for overnight postings confirmed: Y / N.

## Screener
One screening question per sprint question, phrased to disqualify the wrong participant fast.
Prefer past-behavior questions over stated-intent ones.

**Sprint question 1** — *Will a new self-serve user understand the core value prop within 10
seconds of landing on the onboarding flow, without any tooltip or help text?*
> "In the last 90 days, have you personally signed up for a new SaaS product on your own —
> without a demo, trial setup call, or sales rep involved? Walk me through the last time it
> happened: what made you sign up, and what did you do in the first few minutes?"
>
> **Disqualify on:** "No" / can't recall a specific instance / signed up only after a sales-
> assisted trial / all their recent signups were for tools their employer provisioned for them
> (they didn't read the onboarding — IT did the setup).

**Sprint question 2** — *Will a new user complete the key first task (creating their first
project) without hitting the integration-setup step that today causes the most drop-off?*
> "Think about the last time you started using a new tool and had to connect it to something
> else you were already using — like linking accounts, setting up an integration, or importing
> data — before you could actually do anything. Did you complete that step, skip it, or abandon
> the product? Walk me through what happened."
>
> **Disqualify on:** Has never encountered an integration/setup gate in onboarding (can't
> generate signal on this sprint question) / always has IT handle integrations (different
> job-to-be-done).

**Sprint question 3** — *Will a new user choose the guided setup path over skipping straight
to a blank workspace when both are shown up front?*
> "When you sign up for a new tool that offers a walkthrough or tutorial, do you take it or
> skip it? Describe the last time you made that choice — what did you pick and why?"
>
> **Disqualify on:** Always delegates setup to someone else / never self-serves tool adoption
> (their choice behavior is not representative of the target job). Borderline pass: power users
> who always skip — include only if the sprint question is explicitly meant to test that
> segment; otherwise screen out.
