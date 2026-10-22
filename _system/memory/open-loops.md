---
tags:
  - type/memory
last_updated: {{today}}
---
# Open loops

Commitments and follow-ups that cross sessions. One block per loop. Agents read the loops that touch their topic before working and update them in the same turn. Closed loops move to `.archive/_system/open-loops-closed.md` by the consolidation run.

Format:

```
## loop-YYYY-MM-DD-slug
- title: what must happen
- owner: [[Person]]
- opened: YYYY-MM-DD
- due: YYYY-MM-DD        (or none)
- status: open | waiting | closed
- resurface: YYYY-MM-DD  (when the brief shows it again)
- home: [[note where the context lives]]

One paragraph of context. Status updates replace the line below, never append.
Status: ...
```

## loop-{{today}}-fill-the-instance
- title: Fill ORG.md, NOW.md and the five living documents with the onboard skill
- owner: [[{{owner-brain}}]]
- opened: {{today}}
- due: none
- status: open
- resurface: {{review-date}}
- home: [[Knowledge/Company/Company]]

The template ships with a sample company. Run `/company-brain:onboard` to replace it with yours, then archive the sample notes.
Status: open, nothing done yet.
