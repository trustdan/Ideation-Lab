---
id: ts-02
type: test-scenario
created: '2026-08-01'
session: '[[2026-08-01-design-sprint-2-dryrun]]'
verdict: inconclusive
evidence:
  - '[[30-ideas/integration-setup-step-causes-audible-user-confusion.md]]'
  - '[[30-ideas/skip-integration-setup-to-unblock-first-project.md]]'
  - >-
    [[30-ideas/pre-selected-default-with-always-visible-skip-reduces-setup-friction.md]]
sprint-question: >-
  Will a new user complete the key first task (creating their first project)
  without hitting the integration-setup step that today causes the most
  drop-off?
---
# Test scenario: first-project creation clears the integration-setup gate

## Given
A participant qualified by screener Q2 (has personally encountered an integration/account-
connection gate during onboarding) is given the prototype with the redesigned first-project
creation flow — specifically the version that removes or defers the integration-setup step
that historically causes the most drop-off. The prototype must reach the point where a user
would previously have hit that gate.

## When
In Act 4 (Task A) of the [[five-act-interview]], the interviewer says: *"Say you've just
decided to give this a real try. You want to set up your first project — something you'd
actually use this week. Show me what you'd do, talking through your thinking as you go."*
The participant navigates the prototype unassisted. The note-taker tracks whether the
integration-setup screen appears and, if so, what the participant does.

## Then
The participant reaches a recognizable "first project created" end state in the prototype
without encountering the integration-setup gate. Alternatively, if the gate does appear (due
to prototype fidelity limits), the participant verbally indicates they would not have expected
to need it at this point and expresses confusion or reluctance — which is a fail signal
regardless of whether they click through.

Pass signal: participant completes the first-project creation task without pausing at,
questioning, or abandoning an integration/account-connection screen.
Fail signal: participant pauses at an integration prompt, expresses confusion about why it
appears here, backs out, or abandons the task.

## Evidence
