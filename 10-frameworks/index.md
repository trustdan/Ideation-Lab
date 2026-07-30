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
