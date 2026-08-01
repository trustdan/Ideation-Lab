# Design Sprint 2.0 Dry Run — Session Summary

**Date:** 2026-08-01  
**Scenario:** Design Sprint 2 (dry run seeded from scenario design-sprint-2)  
**Goal:** Complete alignment on strategic bets and owner-assigned action items  
**Headcount:** 12 participants · **Duration:** 1 day

---

## Read-Me-First

The idea pool converges on a single urgent design problem: the integration-setup gate blocks users from reaching their first success, and skipping or deferring it is the team's highest-conviction lever. The central tension is that the group's preferred solution — a guided setup flow with an always-visible skip — is built for users who engage with guidance, while early interview evidence shows a meaningful bypass segment that goes straight to a blank workspace. The decision the group faces is whether to prototype the guided path alone, the blank workspace alone, or to treat both as co-design surfaces that must survive each other's failure modes.

---

## Themes

### 1. Defer-and-Skip: Remove the Integration Gate from the Critical Path

Make integration setup explicitly optional from the first moment — pre-select a sensible default, keep the skip always visible, and allow first-project creation without any integration configuration.

**Live tension:** Deferral moves the friction downstream rather than eliminating it. Users who skip integration setup during onboarding will hit the same confusion in session two or three, with no guide present.

**Open challenge:** The "always-visible skip" may not be sufficient — the integration-setup confusion may resurface later. The kill test is whether users who skip can still reach a meaningful first-project end state without re-encountering the gate.

---

### 2. Guided-Path Conviction: The Team Bets on Structured Onboarding

The guided-setup-with-skip storyboard (6 dots vs. 2) is the direction to prototype, borrowing the Linear pattern of a pre-selected default plus always-visible escape.

**Live tension:** A dot-vote reflects team confidence, not user preference. Two load-bearing assumptions are not yet tested: (A1) the vote maps to user behavior, and (A2) users engage with the guided path rather than bypassing it. Interview 2 already falsified A2 for one in five users.

**Challenge verdict — Reshape:** Prototype the guided direction but treat bypass behavior as a required co-design surface. Two kill tests are prescribed before locking prototype hours: a guerrilla corridor test of both storyboards with target-persona users (tests A1), and a deliberate bypass-rate measurement in the next prototype session (tests A2).

---

### 3. Bypass-and-Fallback: Self-Directed Users Need Ambient Support

The blank-workspace experience is not a discarded alternative — it is the de facto onboarding environment for a segment that will skip guidance without reading it. That environment needs ambient contextual cues regardless of which storyboard wins.

**Live tension:** The dot-vote (6 vs. 2) creates organizational pressure to deprioritize the blank-workspace surface. But if 20% of users bypass guidance in a five-person study, the blank workspace is a primary path for a non-trivial segment in production.

**Open challenge:** No ideas in the pool address what the blank workspace should contain. This is also the surface most directly relevant to the "value prop in 10 seconds" sprint question.

---

### 4. Zero-Onboarding Value Clarity: The UI Must Explain Itself

First-screen design must carry explanatory weight — if a user needs a guided tour to understand why the product matters, the UI is failing, not the onboarding.

**Live tension:** Investing in an elaborate onboarding wizard may signal that the first screen is under-designed. The two approaches are not additive; heavy onboarding can mask a weak value proposition rather than fixing it.

**Open challenge:** No prototype or design artifact in the pool addresses first-screen information architecture. This gap is directly relevant to the value-prop-comprehension scenario, which cannot be answered with the current prototype evidence.

---

## Gaps

1. **Blank-workspace design is absent from the pool.** No idea addresses what the blank workspace should contain — ambient cues, empty-state copy, contextual tooltips — despite one of two interview participants ending up there. This is the highest-priority design gap given the sprint goal.

2. **First-screen information architecture is unaddressed.** The "value prop in 10 seconds" HMW has no corresponding design artifact. The pool names the problem but contains no candidate solution beyond the guided flow.

3. **Post-onboarding integration experience is out of scope but load-bearing.** If deferred integration setup reappears in session two, day-30 retention is at risk. The pool contains no ideas about how and when integration setup should be surfaced after initial deferral.

4. **Kill tests have not been run.** Three cheap, decisive validation steps (guerrilla intercept, bypass-rate measurement, Linear-pattern transfer check) are prescribed but not yet completed. Prototype investment decisions are currently made on unverified assumptions.

---

## Recommendation

**Option B, modified — Co-design both surfaces:**

Prototype the guided-setup direction as the primary flow AND define a minimum viable blank-workspace experience as a required co-design surface. Before Friday's test, run the bypass-rate kill test by presenting the choice screen to at least two additional unprimed users. If bypass rate in the next session is ≥2 of 3 users, escalate the blank-workspace surface to equal priority.

This recommendation is falsifiable: if no additional users bypass the guided path in the next session, the guided-only scope (Option A) is justified and blank-workspace work can be deferred.

**Criteria that drive this recommendation:**
1. Bypass segment size matters for the 30-day retention goal. If the bypass segment exceeds 15% of signups, the blank workspace is a primary funnel, not an edge case.
2. The sprint goal is day-1 activation, not storyboard elegance. The winning storyboard should be the one most likely to move day-1 activation.
3. Falsifiability before commitment. Any prototype decision made without running A1 and A2 kill tests is a bet on an untested assumption.

---

## Sprint Questions Answered

> **Note on evidence base:** As of this synthesis, 2 of 5 planned user interviews have been completed. All verdicts below are **inconclusive** — available evidence is directional but insufficient to answer any sprint question with confidence for the full target sample.

**Sprint Question 1: Will a new self-serve user understand the core value prop within 10 seconds of landing on the onboarding flow, without any tooltip or help text?**

Not yet answerable with confidence. The pool contains no interview evidence about 10-second value-prop comprehension. The idea naming this goal is a problem statement, not a test result. A prototype test against this scenario is required before the question can be answered. **Verdict: inconclusive.**

**Sprint Question 2: Will a new user complete the key first task (creating their first project) without hitting the integration-setup step?**

Directional evidence supports yes, but only if the integration gate is explicitly removed or deferred in the prototype. Interview 1 confirms the current flow fails this question — the user paused and verbalized confusion at the integration-setup step. The solution direction is well-specified. Whether the redesigned prototype actually clears the gate has not been tested with the redesign yet. **Verdict: inconclusive pending prototype test; problem confirmed, solution direction well-specified.**

**Sprint Question 3: Will a new user choose the guided setup path over skipping straight to a blank workspace when both are shown up front?**

Mixed evidence — directional lean toward no for a meaningful minority. Interview 2 showed one of two completed interviews resulting in an immediate bypass. The dot-vote represents team preference, not user behavior. With 2 of 5 interviews completed, a 50% bypass rate in the sample so far is too small to generalize but too large to dismiss. **Verdict: inconclusive — current evidence refutes the assumption that the majority will choose guided setup without deliberation.**

---

## Scenario Verdicts

| Scenario | Verdict | Evidence |
|---|---|---|
| test-scenario-first-project-no-integration-gate | **Inconclusive** | Interview 1 confirms the current gate causes blocking confusion; the skip-integration and pre-selected-default ideas specify the solution direction. The prototype with the redesign has not yet been tested. |
| test-scenario-guided-setup-vs-blank-workspace | **Inconclusive** | Interview 2 bypass refutes the pass assumption for at least one user; the dot-vote provides team-preference signal only. 3 of 5 planned interviews remain. |
| test-scenario-value-prop-10-seconds | **Inconclusive** | The value-prop idea names the goal; no interview evidence addresses this scenario. The prototype has not been tested against this criterion. |

---

## Decisions

### Prototype direction: guided setup with always-visible skip, blank workspace preserved as explicit fallback

**Method:** Supervote (dot-vote)  
**Decider:** Design sprint team (6-2 dot vote)  
**Options considered:**
- Guided-setup-with-skip storyboard (6 dots)
- Blank-workspace storyboard (2 dots)

**Outcome:** Prototype the guided-setup-with-skip flow as the default path. The blank workspace is retained as an explicit fallback rather than being discarded.

**Rationale:** Storyboard critique dot-vote favored guided setup 6-2. The challenge note flagged that a team vote is not validated user preference, so the decision preserves the blank-workspace path pending the kill tests prescribed in the guided-setup challenge note.

---

## Actions

| Action Item | Owner | Target Date |
|---|---|---|
| Recruit 3–5 unprimed users for a corridor-intercept storyboard read (kill test for A1: is the 6-2 dot vote a user signal or a team artifact?) | Dan | 2026-08-04 |

---

## Appendix: Idea Titles by Theme

**Theme 1 — Defer-and-Skip**
- Skip integration setup to unblock first project
- Pre-selected default with always-visible skip reduces setup friction
- Integration setup step causes audible user confusion

**Theme 2 — Guided-Path Conviction**
- Guided setup with always-visible skip wins dot vote

**Theme 3 — Bypass-and-Fallback**
- Some users bypass guided option entirely, heading to blank workspace

**Theme 4 — Zero-Onboarding Value Clarity**
- Value prop must land in first 10 seconds without onboarding

---

*Export generated from session vault. Nothing outside the `export/` folder is assumed shareable.*
