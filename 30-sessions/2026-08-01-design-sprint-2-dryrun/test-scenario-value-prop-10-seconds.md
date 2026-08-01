---
id: ts-01
type: test-scenario
created: '2026-08-01'
session: '[[2026-08-01-design-sprint-2-dryrun]]'
verdict: inconclusive
evidence:
  - '[[30-ideas/value-prop-must-land-in-first-10-seconds-without-onboarding.md]]'
sprint-question: >-
  Will a new self-serve user understand the core value prop within 10 seconds of
  landing on the onboarding flow, without any tooltip or help text?
---
# Test scenario: unaided value-prop comprehension in 10 seconds

## Given
A participant who has self-serve-signed-up for at least one SaaS product in the last 90 days
(per screener Q1) is shown the onboarding landing screen of the prototype for the first time,
with no prior explanation of what the product does. Tooltips, help text, and onboarding
overlays are absent from the prototype — this is the "no tooltip or help text" condition the
sprint question specifies.

## When
The interviewer presents the prototype in Act 3 of the [[five-act-interview]] and says:
*"This is very early — think of it as a rough sketch, not a finished product. Before I say
anything else: what do you think this is?"* The note-taker starts a 10-second silent count
from the moment the screen is visible.

## Then
Within 10 seconds, the participant produces an unprompted verbal description of what the
product does or is for that accurately reflects the core value proposition — without the
interviewer confirming, correcting, or elaborating. "Accurately" means their description maps
to the value prop the sprint team agreed on in Day 1; a vague or incorrect description is a
non-pass even if offered quickly.

Pass signal: participant says something like *"Oh, this looks like it helps me [core job]"*
unprompted within 10 seconds.
Fail signal: participant is silent past 10 seconds, asks "what is this?", or offers a
description that misidentifies the product category or job-to-be-done.

## Evidence
