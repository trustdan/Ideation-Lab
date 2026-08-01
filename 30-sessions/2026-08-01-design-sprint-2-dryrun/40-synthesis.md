---
type: synthesis
session: "[[2026-08-01-design-sprint-2-dryrun]]"
created: "2026-08-01"
---

# Synthesis — Design Sprint 2.0 dry run

## Read-me-first

The evidence supports removing integration setup from the first-project critical path, but it does not support treating guided onboarding as the only usable route. The team preferred guided setup 6–2, one captured user became confused at integration setup, and another bypassed guidance entirely. The provoke pass therefore lands on **reshape**: prototype guided setup with an always-visible skip, while making the blank workspace a viable fallback and testing the assumptions before treating the team vote as user preference.

Only two of five planned interview captures are present. Findings below are directional, not final verdicts for the planned study.

## Themes

### `defer-and-skip` — Keep integration setup out of the first-project path

Members:

- [[30-ideas/skip-integration-setup-to-unblock-first-project.md]]
- [[30-ideas/integration-setup-step-causes-audible-user-confusion.md]]

The strongest version explicitly defers integration setup until after a user reaches a meaningful first success. The direct evidence is a user asking whether setup was mandatory. The unresolved risk is displacement: deferring the same confusing step may move abandonment into a later session rather than eliminate it.

### `guided-with-an-exit` — Use a default path without trapping users

Members:

- [[30-ideas/pre-selected-default-with-always-visible-skip-reduces-setup-friction.md]]
- [[30-ideas/guided-setup-with-always-visible-skip-wins-dot-vote.md]]

The team’s 6–2 vote and the Linear-inspired pattern make this the most concrete prototype direction. Its load-bearing assumptions remain untested: the team vote may not predict user preference, users may distrust the pre-selected default, and the visible skip may become a route around the experience rather than reassurance within it.

### `self-directed-fallback` — Guidance must survive being skipped

Members:

- [[30-ideas/some-users-bypass-guided-option-entirely-heading-to-blank-workspace.md]]
- [[30-ideas/value-prop-must-land-in-first-10-seconds-without-onboarding.md]]

One of the two captured interview observations bypassed the guided option. That is too little evidence to estimate a population rate, but enough to reject a prototype that becomes barren when guidance is skipped. The blank workspace needs ambient cues that communicate the product’s value and the next useful action without relying on a tour.

## Unclustered

None. All six ideas contribute to the three decision-relevant themes.

## Cross-cutting tradeoffs

- **Momentum versus deferred debt:** skipping setup gets users to first success faster, but can create a later cliff if setup itself remains confusing.
- **Team conviction versus user evidence:** the dot vote selects a direction for testing; it does not validate user preference.
- **Prototype focus versus route coverage:** building two equally detailed flows would dilute the sprint, but omitting the blank fallback could make tests inconclusive when users bypass guidance.
- **Guidance versus self-evidence:** a guided path can accelerate novices, while a strong first screen should still explain value to users who ignore it.

## Gaps

1. No capture tests unaided value comprehension in the first 10 seconds.
2. No idea redesigns the integration-setup step itself or specifies when deferred setup returns.
3. The blank-workspace cues are a requirement, not yet a concrete design.
4. Only two of five planned interview captures are available.
5. Nothing in the current pool measures the long-term goal’s 30-day retention component.

## Recommendation & decision framing

Choose a tightly scoped hybrid prototype:

1. Make guided setup the default route.
2. Pre-select one sensible choice and keep skip continuously visible.
3. Remove integration setup from the first-project critical path and state clearly that it is deferred.
4. Give the blank workspace a minimal but usable fallback: one clear value statement, one primary next action, and contextual guidance that does not require a tour.

Before treating this direction as validated, run the challenge note’s cheap kill tests: show both storyboard directions without framing to 3–5 target users, and measure unprompted bypass behavior in the remaining interviews. Proceed with the hybrid if users can explain the value and complete the first task; reshape again if guidance is ignored or deferred setup recreates confusion.

The decision is falsifiable: if the remaining tests show that users consistently choose and complete the guided path without setup confusion, the fallback can remain minimal. If users bypass guidance or fail to understand the first screen, the blank-workspace surface must become a primary design path.

## Sprint questions answered

### 1. Will users understand the core value proposition within 10 seconds without tooltip or help text?

**Not yet answerable.** None of the two available interview captures records unaided first-screen comprehension. Add a timed, no-explanation first-impression probe to the remaining interviews.

### 2. Will users create their first project without hitting the integration-setup step?

**Not yet answerable for the proposed redesign.** Current-flow evidence confirms that integration setup causes audible uncertainty. The ideas provide a plausible remedy—defer the step and expose skip—but no captured test shows a user completing the first project with that remedy in place.

### 3. Will users choose guided setup over a blank workspace when both are offered?

**Not yet answerable.** The 6–2 dot vote measures team preference. One of the two available user observations bypassed guidance, proving that the fallback matters but not establishing the eventual choice rate. Record unprompted route selection across the remaining interviews.

## Scenario verdicts

No test-scenario notes are attached to this session yet, so no formal `validated`, `refuted`, or `inconclusive` frontmatter verdict can be written. The evidence above should be linked when coach-prep creates the scenarios and later interviews support a formal verdict.
