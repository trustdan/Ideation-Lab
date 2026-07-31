---
type: test-scenario
session: "[[2099-01-01-fixture-session]]"
id: ts-01
sprint-question: Will users trust an AI-drafted follow-up email enough to send it unedited?
verdict: validated
evidence: ["[[fixture-interview-notes]]"]
created: 2026-07-31
---
# Test scenario: AI-drafted follow-up email

## Given
A user has just finished a call with a prospect.

## When
They ask the assistant to draft a follow-up email.

## Then
They send it with zero edits.

## Evidence
- [[fixture-interview-notes]] — 4 of 5 test users sent the draft unedited.
