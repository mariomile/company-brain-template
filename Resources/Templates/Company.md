---
tags:
  - type/company
  - crm/{{relationship}}
industry: 
stage: 
website: 
location: 
owner: "[[{{owner}}]]"
customer_of: 
partner_of: 
competitor_of: 
since: 
confidentiality: internal
up: "[[companies-index]]"
---
# {{title}}

## Now

<!-- What they are to us, the state of the relationship, what is open. -->

- 

## People

- 

## Timeline

- 

## All notes about {{title}}

```base
filters:
  or:
    - 'project == link("{{title}}")'
    - 'customer == link("{{title}}")'
    - 'file.hasLink(link("{{title}}"))'
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
