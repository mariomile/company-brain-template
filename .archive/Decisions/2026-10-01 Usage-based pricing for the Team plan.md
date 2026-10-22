---
sample: true
status: accepted
decided: 2026-10-01
decider: "[[Ada Rossi]]"
project: none
source: "pricing review meeting, 2026-09-30 (no minutes)"
supersedes: 
review_due: 2027-04-01
confidentiality: internal
tags:
  - type/decision
  - domain/market
  - product/billing
---
# Usage-based pricing for the Team plan

## Context

- Team plan was flat at €149 per month; 60% of Team customers used under 20% of the included events [source: billing export 2026-09; since: 2026-09-30]
- Three prospects in Q3 lost on "too expensive for our volume" [source: sales notes Q3; since: 2026-09-30]

## Options

- **A.** Keep flat, add a cheaper Starter tier.
- **B.** Usage-based: base fee plus events, with a cap.
- **C.** Do nothing.

## Decision

B. Base €49 plus €0.80 per 10k events, capped at €299. Enterprise unchanged.

## Consequences

- Gained: lower entry price, revenue scales with value delivered.
- Lost or risked: revenue dip for 2 quarters if existing Team customers are light users; forecasting is harder.
- Cost: billing changes, 3 weeks of engineering.

## Revisit when

- Team MRR after 2 quarters is below 90% of the pre-change level.
- Support tickets about bills exceed 5 per month.

## Dissent

[[Ben Okafor]] preferred A: simpler to explain during onboarding. Recorded, overruled.
