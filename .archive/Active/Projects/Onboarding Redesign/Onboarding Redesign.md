---
sample: true
project: "Onboarding Redesign"
status: active
owner: "[[Ben Okafor]]"
review_due: 2026-10-30
last_verified: 2026-10-16
started: 2026-09-01
target: 2026-11-15
tags:
  - type/project
  - domain/product
  - product/onboarding
up: "[[project-index]]"
last_updated: 2026-10-16
---
# Onboarding Redesign

> Cut time-to-first-value for new workspaces from 9 days to 3.

**Why it matters:** non-activated workspaces churn at 82% by day 90 ([[Activation]]).
**Success looks like:** median TTFV of 3 days on workspaces created after launch, measured 30 days after launch. Baseline: 9 days [source: [[Input/Meetings/2026-10-14 Weekly product sync]]; since: 2026-10-14].

## Now

- State: build started 2026-10-07; guided first-funnel flow in review; dashboard-share prompt not started
- Next step: ship guided funnel to 10% of new workspaces by 2026-10-24
- Blocked by: none

## People

- Owner: [[Ben Okafor]]
- Team: two engineers, one designer (to verify: names)
- Stakeholders: [[Ada Rossi]]; customer voice [[Jane Doe]]

## Decisions

- [[2026-10-01 Usage-based pricing for the Team plan]]: pricing simplicity during onboarding was the dissent here

## Open questions

- Do we show the share prompt before or after the first funnel?

## Tasks

- [ ] Guided funnel to 10% · Ben · 2026-10-24
- [ ] Walk [[Jane Doe]] through the new flow · Ben · after launch
- [x] Discovery interviews, 6 customers · done 2026-09-26

## Timeline

- 2026-10-14: weekly sync fixed the success metric and baseline, see [[Input/Meetings/2026-10-14 Weekly product sync|minutes]]
- 2026-10-10: [[Input/Feedback/2026-10-10 Northwind onboarding stalled|Northwind feedback]] confirmed the problem
- 2026-09-01: project started

## All notes of this project

```base
filters:
  and:
    - 'project == link("Onboarding Redesign")'
views:
  - type: table
    name: Notes
    order:
      - file.name
      - date
      - tags
    sort:
      - property: date
        direction: DESC
```
