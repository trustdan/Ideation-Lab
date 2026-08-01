---
type: synthesis
session: "[[2026-08-01-design-sprint-2-dryrun]]"
created: "2026-08-01"
---

# Synthesis — Design Sprint 2 Dry-Run (2026-08-01)

## Read-Me-First

The idea pool converges on a single urgent design problem: the integration-setup gate blocks users from reaching their first success, and skipping or deferring it is the team's highest-conviction lever. The central tension is that the group's preferred solution — a guided setup flow with an always-visible skip — is built for users who engage with guidance, while early interview evidence shows a meaningful bypass segment that goes straight to a blank workspace. The decision the group faces is whether to prototype the guided path alone, the blank workspace alone, or to treat both as co-design surfaces that must survive each other's failure modes.

---

## Themes

### 1. Defer-and-Skip: Remove the Integration Gate from the Critical Path

**Members:**
- [[30-ideas/skip-integration-setup-to-unblock-first-project.md]]
- [[30-ideas/pre-selected-default-with-always-visible-skip-reduces-setup-friction.md]]
- [[30-ideas/integration-setup-step-causes-audible-user-confusion.md]]

**Strongest variant:** Make integration setup explicitly optional from the first moment — pre-select a sensible default, keep the skip always visible, and allow first-project creation without any integration configuration.

**Live tension:** Deferral moves the friction downstream rather than eliminating it. Users who skip integration setup during onboarding will hit the same confusion in session two or three, with no guide present. The sprint question is answered at the onboarding layer; the underlying UX debt is not.

**Open challenges:** The challenge note flags that "always-visible skip" may not be sufficient — the integration-setup confusion may resurface later. The kill test for this theme is whether users who skip can still reach a meaningful first-project end state without re-encountering the gate.

---

### 2. Guided-Path Conviction: The Team Bets on Structured Onboarding

**Members:**
- [[30-ideas/guided-setup-with-always-visible-skip-wins-dot-vote.md]]

**Strongest variant:** The guided-setup-with-skip storyboard (6 dots vs. 2) is the direction to prototype, borrowing the Linear pattern of a pre-selected default plus always-visible escape.

**Live tension:** A dot-vote reflects team confidence, not user preference. The challenge note identifies two load-bearing assumptions that are not yet tested: (A1) the vote maps to user behavior, and (A2) users engage with the guided path rather than bypassing it. Interview 2 already falsified A2 for one in five users.

**Open challenges:** The challenge verdict is **Reshape** — prototype the guided direction but treat bypass behavior as a required co-design surface. Two kill tests are prescribed before locking prototype hours: a guerrilla corridor test of both storyboards with target-persona users (tests A1), and a deliberate bypass-rate measurement in the next prototype session (tests A2).

---

### 3. Bypass-and-Fallback: Self-Directed Users Need Ambient Support

**Members:**
- [[30-ideas/some-users-bypass-guided-option-entirely-heading-to-blank-workspace.md]]

**Strongest variant:** The blank-workspace experience is not a discarded alternative — it is the de facto onboarding environment for a segment that will skip guidance without reading it. That environment needs ambient contextual cues regardless of which storyboard wins.

**Live tension:** The dot-vote (6 vs. 2) creates organizational pressure to deprioritize the blank-workspace surface. But if 20% of users bypass guidance in a five-person study, the blank workspace is a primary path for a non-trivial segment in production.

**Open challenges:** No ideas in the pool address what the blank workspace should contain. This is also the surface most directly relevant to the "value prop in 10 seconds" sprint question — a well-designed empty state may answer that question without any onboarding overlay.

---

### 4. Zero-Onboarding Value Clarity: The UI Must Explain Itself

**Members:**
- [[30-ideas/value-prop-must-land-in-first-10-seconds-without-onboarding.md]]

**Strongest variant:** First-screen design must carry explanatory weight — if a user needs a guided tour to understand why the product matters, the UI is failing, not the onboarding.

**Live tension:** This idea is in tension with the guided-path theme: investing in an elaborate onboarding wizard may be a signal that the first screen is under-designed. The two approaches are not additive; heavy onboarding can mask a weak value proposition rather than fixing it.

**Open challenges:** No prototype or design artifact in the pool addresses first-screen information architecture. This gap is directly relevant to test-scenario ts-01 (value-prop comprehension in 10 seconds), which cannot be answered with the current prototype evidence.

---

## Unclustered

None. All six ideas are assigned to themes.

---

## Cross-Cutting Tradeoffs

**1. Team conviction vs. user behavior signal**
The dot-vote creates organizational confidence in the guided path. Early interview evidence (1-of-2 completed interviews showing bypass behavior) suggests that confidence may not be calibrated to user behavior. Every decision made from the vote alone risks optimizing for a path a significant user segment never takes.

**2. Deferral vs. elimination**
Skipping the integration-setup step during onboarding solves the onboarding drop-off metric but moves the friction to session two or three. The sprint goal is day-1 activation and 30-day retention; a deferred gate that causes churn in week two is not a win against either metric.

**3. Guided path vs. blank workspace as complementary surfaces**
The two storyboard directions were voted on as alternatives. The bypass finding suggests they are actually co-required: the guided path is the modal path, but the blank workspace is the environment for a bypass segment that will exist regardless of design. Prototyping only one and assuming the other can be patched later is the highest-risk sequencing choice.

---

## Gaps

1. **Blank-workspace design is absent from the pool.** No idea addresses what the blank workspace should contain — ambient cues, empty-state copy, contextual tooltips — despite one of two interview participants ending up there. This is the highest-priority design gap given the sprint goal.

2. **First-screen information architecture is unaddressed.** The "value prop in 10 seconds" HMW has no corresponding design artifact. The pool names the problem but contains no candidate solution beyond the guided flow, which explicitly uses onboarding to carry value-communication weight.

3. **Post-onboarding integration experience is out of scope but load-bearing.** If deferred integration setup reappears in session two, day-30 retention is at risk. The pool does not contain any ideas about how and when integration setup should be surfaced after initial deferral.

4. **Kill tests have not been run.** The challenge note prescribes three cheap, decisive validation steps (guerrilla intercept, bypass-rate measurement, Linear-pattern transfer check). None of these are represented as completed evidence in the pool. Prototype investment decisions are currently made on unverified assumptions.

---

## Recommendation & Decision Framing

### What to decide
Whether to prototype the guided-setup direction alone, or to prototype both the guided path and the blank-workspace surface as co-required design outputs before Friday's user test.

### Real options

**Option A — Guided path only (current default)**
Prototype the 6-dot winning storyboard. Accept that bypass users land in an undesigned blank workspace. Run kill tests after prototype is built. Risk: if bypass rate holds at 20%+ in production, there is no fallback and the blank-workspace churn goes uninstrumented.

**Option B — Co-design both surfaces**
Prototype the guided path *and* define a minimum viable blank-workspace experience (ambient empty-state cues, at minimum). This adds scope but closes the gap that the challenge note identifies as the most probable failure mode. The two surfaces share most design decisions; the marginal cost is lower than prototyping them independently.

**Option C — Run kill tests first, then decide**
Delay prototype commitment by 2–4 hours to run the guerrilla corridor test (tests A1) and the bypass-rate measurement (tests A2). This is lower-risk but compresses the prototype build window. Recommended only if the team has schedule flexibility.

### Criteria to decide by
1. **Bypass segment size matters for the 30-day retention goal.** If the bypass segment is >15% of signups, the blank workspace is a primary funnel, not an edge case.
2. **The sprint goal is day-1 activation, not storyboard elegance.** The winning storyboard should be the one most likely to move day-1 activation, not the one the team finds most satisfying to build.
3. **Falsifiability before commitment.** Any prototype decision made without running A1 and A2 kill tests is a bet on an untested assumption. The challenge note prescribes these as cheap and decisive.

### Recommendation
**Option B, modified:** Prototype the guided-setup direction as the primary flow AND define a minimum viable blank-workspace experience as a required co-design surface. Before Friday's test, run the bypass-rate kill test by presenting the choice screen to at least two additional users unprimed. If bypass rate in the next session is ≥2 of 3 users, escalate the blank-workspace surface to equal priority. This recommendation is falsifiable: if no additional users bypass the guided path in the next session, Option A is justified and the blank-workspace scope can be deferred.

---

## Sprint Questions Answered

> **Note on evidence base:** As of this synthesis, 2 of 5 planned user interviews have been completed. Verdicts marked **inconclusive** reflect that the available evidence is directional but insufficient to answer the sprint question with confidence for the full target sample.

**Sprint Question 1: Will a new self-serve user understand the core value prop within 10 seconds of landing on the onboarding flow, without any tooltip or help text?**

**Not yet answerable with confidence.** The pool contains no interview evidence about 10-second value-prop comprehension. The HMW note ([[30-ideas/value-prop-must-land-in-first-10-seconds-without-onboarding.md]]) names the goal but is a problem statement, not a test result. Test-scenario `test-scenario-value-prop-10-seconds` has no evidence field populated. Verdict: **inconclusive** — a prototype test against this scenario is required before this question can be answered.

**Sprint Question 2: Will a new user complete the key first task (creating their first project) without hitting the integration-setup step?**

**Directional evidence supports yes, but only if the integration gate is explicitly removed or deferred in the prototype.** Interview 1 ([[30-ideas/integration-setup-step-causes-audible-user-confusion.md]]) confirms the current flow fails this question — the user paused and verbalized confusion at the integration-setup step. The HMW ([[30-ideas/skip-integration-setup-to-unblock-first-project.md]]) and Lightning Demo pattern ([[30-ideas/pre-selected-default-with-always-visible-skip-reduces-setup-friction.md]]) provide candidate solutions. Whether the redesigned prototype actually clears the gate depends on prototype fidelity and has not been tested with the redesign yet. Verdict: **inconclusive** pending prototype test, but the problem is confirmed and the solution direction is well-specified.

**Sprint Question 3: Will a new user choose the guided setup path over skipping straight to a blank workspace when both are shown up front?**

**Mixed evidence — directional lean toward no for a meaningful minority.** Interview 2 ([[30-ideas/some-users-bypass-guided-option-entirely-heading-to-blank-workspace.md]]) showed one of two completed interviews resulting in an immediate bypass. The dot-vote ([[30-ideas/guided-setup-with-always-visible-skip-wins-dot-vote.md]]) represents team preference, not user behavior. With 2 of 5 interviews completed, a 50% bypass rate in the sample so far is too small to generalize but too large to dismiss. Verdict: **inconclusive** — the test-scenario requires data from all 5 interviews; current evidence refutes the assumption that the majority will choose guided setup without deliberation.

---

## Scenario Verdicts

| Scenario | Verdict | Cited Evidence |
|---|---|---|
| test-scenario-first-project-no-integration-gate | **inconclusive** | [[30-ideas/integration-setup-step-causes-audible-user-confusion.md]] confirms the current gate causes blocking confusion (Interview 1); [[30-ideas/skip-integration-setup-to-unblock-first-project.md]] and [[30-ideas/pre-selected-default-with-always-visible-skip-reduces-setup-friction.md]] specify the solution direction. Prototype with the redesign has not yet been tested. |
| test-scenario-guided-setup-vs-blank-workspace | **inconclusive** | [[30-ideas/some-users-bypass-guided-option-entirely-heading-to-blank-workspace.md]] (Interview 2 bypass) refutes the pass assumption for at least one user; [[30-ideas/guided-setup-with-always-visible-skip-wins-dot-vote.md]] provides team-preference signal only. 3 of 5 planned interviews remain. |
| test-scenario-value-prop-10-seconds | **inconclusive** | [[30-ideas/value-prop-must-land-in-first-10-seconds-without-onboarding.md]] names the goal; no interview evidence addresses this scenario. Prototype has not been tested against this criterion. |

---

## Run Report

- **Idea count:** 6 ideas + 1 challenge note (challenge not clustered)
- **Themes:** 4 — defer-and-skip (3 members), guided-path-conviction (1 member), bypass-and-fallback (1 member), zero-onboarding-value-clarity (1 member)
- **Unclustered:** 0
- **Challenges incorporated:** 1 (challenge on guided-setup dot-vote; verdict Reshape; reflected in recommendation and tradeoffs)
- **theme: edits to apply:** 6 ideas
- **Sprint questions answered:** 3 of 3 (all inconclusive — evidence base is 2 of 5 planned interviews)
- **Scenario verdicts assigned:** 3 of 3 (all inconclusive)
- **Decision for the group:** Commit to co-designing both the guided-setup path and a minimum viable blank-workspace surface before Friday's prototype test, and run the bypass-rate kill test with at least two additional unprimed users before locking prototype scope.
