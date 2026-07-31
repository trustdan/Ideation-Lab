---
type: meta
created: 2026-07-30
---
# Framework library

Static index (canonical — renders everywhere):
- [[crazy-8s|Crazy 8s]] — diverge · 15m · volume sketching
- [[how-might-we|How Might We]] — diverge · 20m · problem reframing
- [[dot-voting|Dot voting]] — converge · 10m · cheap prioritization
- [[bet-brief|Bet brief]] — converge · 35m · write up shortlisted bets (seed stub)
- [[premortem|Premortem]] — decide · 25m · failure hunting
- [[commitment-round|Commitment round]] — commit · 40m · owner + first action + date (seed stub)
- [[design-sprint-day-by-day|Design sprint: day by day]] — n/a · n/a · Knapp's five-day arc, orientation
- [[design-sprint-2-agenda|Design sprint 2.0 agenda]] — n/a · n/a · four-day agenda with timings
- [[time-recovery-playbook|Time recovery playbook]] — n/a · n/a · what to cut when the room is behind
- [[five-act-interview|Five-act interview]] — decide · 60m · the Friday test structure
- [[note-and-vote|Note and vote]] — converge · 15m · quiet decision-making
- [[sailboat-retrospective|Sailboat retrospective]] — converge · 55m · retro via drivers/anchors/risks/goal
- [[gradients-of-agreement|Gradients of agreement]] — decide · 30m · 8-point alignment scale beyond yes/no
- [[divergent-vs-convergent|Divergent vs. convergent thinking]] — n/a · n/a · which cognitive mode a block calls for
- [[neuroinclusive-facilitation|Neuroinclusive facilitation]] — n/a · n/a · standing accessibility adaptations for every session
- [[agenda-60min-problem-framing|60-min problem-framing agenda]] — n/a · n/a · vague challenge to one problem statement
- [[agenda-90min-ideation|90-min ideation agenda]] — n/a · n/a · HMW through sketching to a shortlist
- [[dominant-participant-playbook|Dominant participant playbook]] — n/a · n/a · rebalancing airtime without defensiveness
- [[silence-playbook|Silence / low-engagement playbook]] — n/a · n/a · what to do with a room that won't answer
- [[personal-conflict-playbook|Personal-conflict playbook]] — n/a · n/a · de-escalating attacks on people, not ideas
- [[solution-jumping-playbook|Solution-jumping playbook]] — n/a · n/a · parking premature fixes, back to the problem
- [[low-energy-playbook|Low-energy room playbook]] — n/a · n/a · re-energizing a flagging room
- [[voting-tie-playbook|Voting-tie playbook]] — n/a · n/a · breaking a deadlocked vote fast

Live view (Dataview enhancement; safe to ignore outside Obsidian):

```dataview
TABLE phase, timebox, group-size, status
FROM "10-frameworks"
WHERE type = "framework"
SORT phase ASC, file.name ASC
```

Adding a framework: copy `90-meta/templates/framework.md`, fill frontmatter honestly
(`timebox`, `group-size` are what the facilitator schedules by), add a line to the static
list above.
