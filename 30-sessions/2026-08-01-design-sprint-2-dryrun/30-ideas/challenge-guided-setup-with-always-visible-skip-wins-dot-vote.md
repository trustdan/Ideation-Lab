---
type: challenge
session: "[[2026-08-01-design-sprint-2-dryrun]]"
phase: converge
targets:
  - "[[30-ideas/guided-setup-with-always-visible-skip-wins-dot-vote.md]]"
created: "2026-08-01"
---

# Challenge: Guided Setup with Always-Visible Skip Wins Dot-Vote

## 1. Assumption Inventory

| # | Assumption | Load-bearing? |
|---|-----------|---------------|
| A1 | A 6-vs-2 dot-vote from a single sprint session reliably signals which direction users will prefer, not just which direction the team prefers to build. | ⚠️ **LOAD-BEARING** |
| A2 | Users who encounter the guided setup will actually engage with it rather than bypassing it — i.e., the guided path is the modal path, not an edge case. | ⚠️ **LOAD-BEARING** |
| A3 | The Linear-borrowed pattern (pre-selected default + always-visible skip) transfers to this product's context, user mental models, and job-to-be-done. | ⚠️ **LOAD-BEARING** |
| A4 | "Always-visible skip" is sufficient to prevent users from feeling trapped; no further friction reduction is needed at the integration-setup step. | — |
| A5 | The blank-workspace-with-contextual-tips direction is a genuine alternative, not a complementary layer that the winning direction still needs. | — |
| A6 | Dot-vote scores from storyboard critique correlate with downstream prototype test outcomes (i.e., team intuition is calibrated). | — |
| A7 | Prototyping the guided-setup direction first is lower-risk than prototyping the blank-workspace direction, even given the bypass behavior observed in Interview 2. | — |

---

## 2. Kill Tests

**For A1 — The dot-vote reflects user preference, not team preference**

*Kill test:* Run a 5-minute guerrilla corridor intercept (3–5 target-persona users, not sprint participants). Show each storyboard as a static image sequence — no framing, no facilitation — and ask: "Walk me through what you'd do here." If the guided-setup direction does not produce faster, more confident narration, the vote result is a team artifact, not a user signal. Cost: 2–4 hours. Decisive: yes — if users pause or express the same "do I have to do this?" confusion on the guided path, A1 is false.

**For A2 — Users will engage with the guided path, not bypass it**

*Kill test:* Replay Interview 2's bypass behavior deliberately. In the next round of prototype testing, present the guided-setup screen to 3 users without verbal priming and measure: how many scroll past it or click away within 8 seconds. One session already produced this behavior in 5 interviews (20% bypass rate observed). If ≥2 of the next 3 users bypass it, the guided path's reach is narrower than the dot-vote implies. Cost: repurpose one scheduled test slot. Decisive: yes — prototype investment in guidance is wasted if a meaningful user segment never sees it.

**For A3 — The Linear pattern transfers**

*Kill test:* Pull 3 Linear users (or users of analogous onboarding wizards) from the existing customer list and ask a single question: "When you saw the pre-selected default, did you trust it or override it?" If the majority report overriding or ignoring the default, the borrowed mechanic's trust premise does not transfer. Cost: three 10-minute calls or a Slack DM survey. Decisive: yes — if users distrust pre-selection in this domain, the "removes decision tax" framing collapses.

---

## 3. Premortem

*It is twelve months later. The guided-setup-with-always-visible-skip prototype shipped and onboarding metrics did not improve. Here is what happened, most probable first:*

**Cause 1 — The bypass segment grew, not shrank.**
The prototype was optimized for users who read and engage. In production, a disproportionate share of new signups (power users, developers, people who clicked an ad expecting immediate utility) skipped the guided flow on first screen-load. The always-visible skip became a "skip everything" button. The blank-workspace experience — never improved because it "lost" the dot-vote — remained barren. Churn concentrated in this segment, and the team hadn't instrumented it because they expected the guided path to be the main funnel.

**Cause 2 — The integration-setup gate was deferred but not redesigned.**
The guided flow surfaced integration setup later rather than eliminating the confusion. Users who skipped integration during onboarding hit the same "wait, do I have to do this now?" moment in their second or third session, with no guide present. The friction moved downstream instead of being resolved. The sprint question ts-02 was answered at the onboarding layer but the underlying UX debt was untouched.

**Cause 3 — The Linear pattern created mismatched expectations.**
Linear's pre-selected default works because Linear's defaults are deeply opinionated and trusted by its persona (technical PMs). This product's persona has different domain expectations; the pre-selected default felt arbitrary rather than expert. Users changed the default, which broke the "no decision tax" promise, and the guided flow felt longer, not shorter, than a blank workspace would have.

---

## 4. Reframes

**Reframe 1 — HMW design for the skipper, not against them?**
The bypass behavior in Interview 2 is not a problem to suppress — it may be the most honest signal about user intent. What if the blank workspace *is* the product for a meaningful segment, and guided onboarding is an opt-in overlay rather than the default path? Invert the vote: prototype the blank workspace with ambient contextual cues as the primary flow, and treat guided setup as a secondary mode users can summon.

**Reframe 2 — HMW make the skip the value, not the escape hatch?**
Right now "always-visible skip" is framed as safety netting — reassurance that users aren't trapped. But what if skipping integration setup *is* the product's main value proposition for new users? Lean into it: the first-run experience explicitly names what you're skipping and why that's fine. This reframes deferred setup from friction-reduction to a feature.

**Reframe 3 — HMW use the dot-vote gap as a design constraint, not a decision?**
The 6-vs-2 gap might mean: "build guided setup, ignore blank workspace." Or it might mean: "the team is more confident about guided setup — so that's the one that needs the most testing, not the least." Redirect prototype effort toward the higher-conviction direction's failure modes (the bypass, the integration deferral) rather than its surface mechanics.

---

## 5. Steelman of the Opposite

The strongest case for *not* committing to the guided-setup direction — and instead prototyping the blank-workspace-with-contextual-tips direction — is already present in the session's own evidence. One in five interviewed users bypassed the guided option without reading it. That is not a rounding error in a five-person study; it is a reproducible behavioral pattern. Contextual tips embedded in a blank workspace are ambient by design: they require no user decision to engage, they do not create a "skip" affordance that signals the flow is optional, and they do not depend on the user trusting a pre-selected default. The blank-workspace direction also directly addresses the "value prop in 10 seconds" HMW — a well-designed empty state communicates purpose without a tutorial. If the team builds only the guided path and the bypass segment grows in production, there is no fallback because the alternative direction was never developed. The 2-dot score may reflect the team's comfort level, not the approach's ceiling.

---

## 6. Verdict

**Reshape.** The dot-vote direction is worth prototyping, but not in isolation — the bypass finding makes the blank-workspace experience a required co-design surface, not a discarded loser, and the two load-bearing assumptions (team vote ≠ user preference; users engage with guidance) both need a cheap kill test before prototype hours are locked in.
