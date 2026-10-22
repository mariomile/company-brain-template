---
project: "{{title}}"
status: active
owner: {{owner_link}}
review_due: {{review_due}}
last_verified: {{today}}
started: {{today}}
target: 
tags:
  - type/project
  - domain/{{domain}}
up: "[[project-index]]"
last_updated: {{today}}
---
# {{title}}

> One sentence: the outcome this project exists to produce.

**Why it matters:** 
**Success looks like:** (a measurable condition, with the baseline)

## Now

<!-- Current state in 3 to 6 lines. Replace, do not append. -->

- State: 
- Next step: 
- Blocked by: none

## People

- Owner: {{owner_ref}}
- Team: 
- Stakeholders: 

## Decisions

<!-- One line per decision, linked to Decisions/. -->

- 

## Open questions

- 

## Tasks

- [ ] 

## Timeline

<!-- Dated events, newest first, with links to minutes and documents. -->

- {{today}}: project created.

## All notes of this project

```base
filters:
  and:
    - 'project == link("{{title}}")'
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
