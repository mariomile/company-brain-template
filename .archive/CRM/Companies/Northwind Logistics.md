---
sample: true
tags:
  - type/company
  - crm/customer
  - customer/midmarket
industry: logistics
stage: customer
website: https://northwind.example
location: Verona
owner: "[[Ben Okafor]]"
customer_of: "[[Lumen Analytics]]"
since: 2025-03-01
confidentiality: internal
up: "[[companies-index]]"
---
# Northwind Logistics

## Now

- Team plan, 2 workspaces, 140 people; renewal 2027-03 [source: billing export 2026-10-01; since: 2026-10-01]
- Risk: second workspace never activated [source: [[Input/Feedback/2026-10-10 Northwind onboarding stalled]]; since: 2026-10-10]

## People

- [[Jane Doe]], Head of Operations, champion

## Timeline

- 2026-10-10: onboarding stalled on workspace 2, ticket #4821
- 2025-03-01: became a customer

## All notes about Northwind Logistics

```base
filters:
  or:
    - 'customer == link("Northwind Logistics")'
    - 'file.hasLink(link("Northwind Logistics"))'
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
