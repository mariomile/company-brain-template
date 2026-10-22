---
tags:
  - type/playbook
  - domain/knowledge
owner: "[[Ada Rossi]]"
review_due: 2027-04-15
last_verified: 2026-10-15
applies_to: ["everyone"]
confidentiality: internal
---
# Record a decision

> Use the day a decision is taken, by whoever took it. Five minutes.

## Before you start

- Is it a decision (changes what we do) or a definition or an opinion? Definitions go in the [[Glossary]] or a concept; opinions in the project note's open questions.

## Steps

1. Create `Decisions/YYYY-MM-DD Short title.md` from `_system/templates/Decision.md`, or ask an agent: "record the decision: we chose X over Y because Z".
2. Fill Context with facts and sources, Options with the ones actually considered, the Decision in one paragraph, Consequences honestly, Revisit when as conditions.
3. Write the dissent in the dissenter's words. Empty is a fact.
4. Set `status: accepted` and `decider`. If it replaces an older decision, set `supersedes` and mark the old one `status: superseded`.
5. Link it from the project note's Decisions section and, if it changes a living document, add the dated fact line there.

## Done when

- The record exists, is linked from its project or living document, and `brain health` shows no proposed decision older than 14 days.

## Known failure modes

- Writing it a week later from memory: the context is gone. Record the day of.
- Hiding the dissent: the next person will re-litigate it.
