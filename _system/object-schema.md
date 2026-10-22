---
tags:
  - type/reference
owner: "[[{{owner-brain}}]]"
review_due: {{review-date}}
confidentiality: internal
last_updated: {{today}}
---
# Object schema

> Which frontmatter properties each `#type/*` carries, beyond the mandatory `tags`. Changing a property set is a decision.
>
> **Golden rule:** if a property is not needed for a query, a filter in a view or a governance check, it does not go in frontmatter. It goes in the body.

## Common to every note

| Property | Required | Notes |
|---|---|---|
| `tags` | ✅ | 1 to 4, from `_tags.md`, including one `type/*` |
| `confidentiality` | no | `public · internal · confidential · restricted`; absent means `internal` |
| `up` | recommended | `"[[Parent or MOC]]"`, quoted |
| `related` | no | list of quoted wikilinks |
| `aliases` | no | only when people really use another name |

Agent-managed files only (`_system/**`, project notes, living documents): `created_by`, `last_edited_by`, `last_updated`. Never on human notes unless asked.

## Governance block

On every **living document** (`type/living`, `type/playbook`, `type/policy`, `type/project`, `type/goal`, `type/index` in `_system/indices/`):

```yaml
owner: "[[Person]]"
review_due: YYYY-MM-DD
last_verified: YYYY-MM-DD
```

Default review cadence, used by the `verify` flow to bump `review_due` from `last_verified`:

| Type | Cadence |
|---|---|
| `type/living` in `Knowledge/Company/` | 90 days (`NOW.md`: 14 days) |
| `type/playbook` | 180 days |
| `type/policy` | 365 days |
| `type/project` with `status: active` | 14 days |
| `type/goal` | 90 days |
| `type/index` | 30 days |
| `type/concept` | no date; `status: disproven` when overturned |

## Per type

### `type/living` (Knowledge/Company/)

The five living documents: `Company.md`, `Product.md`, `Customers.md`, `How We Work.md`, `Glossary.md` (the last carries `type/glossary`). Sections are fixed by the templates; content is yours.

```yaml
tags: [type/living, domain/product]
owner: "[[Ben Okafor]]"
review_due: 2027-01-14
last_verified: 2026-10-16
confidentiality: internal
```

### `type/project`

```yaml
project: "Onboarding Redesign"
status: active            # active · backlog · paused · done
owner: "[[Ben Okafor]]"
review_due: 2026-10-30
last_verified: 2026-10-16
tags: [type/project, domain/product, product/onboarding]
started: 2026-09-01
target: 2026-11-15         # optional
```

### `type/decision`

```yaml
status: accepted           # proposed · accepted · superseded · reversed
decided: 2026-10-01
decider: "[[Ada Rossi]]"
project: "[[Onboarding Redesign]]"   # or none
source: "[[2026-09-30 Pricing review]]"
supersedes: "[[2026-03-12 Flat pricing]]"   # optional
review_due: 2027-04-01     # when to revisit, optional but recommended
tags: [type/decision, domain/market]
```

File name: `YYYY-MM-DD Short title.md`.

### `type/meeting`

```yaml
date: 2026-10-14
project: "[[Onboarding Redesign]]"   # or none, or to verify
attendees: ["[[Ada Rossi]]", "[[Ben Okafor]]"]
source: "[[Input/Meetings/Granola/2026-10-14 Weekly product sync]]"   # the transcript, if any
tags: [type/meeting, domain/product]
```

File name: `YYYY-MM-DD Title.md`. One meeting, one note. If the same meeting arrives from two sources, keep one note and link the other as backup.

### `type/conversation`

```yaml
date: 2026-10-13
channel: email             # email · slack · teams · ticket · call
project: "[[Northwind Logistics]]"
participants: ["[[Jane Doe]]"]
source: "email thread 'Renewal terms', 2026-10-13"
tags: [type/conversation, domain/customers]
```

### `type/document`, `type/research`

```yaml
source: https://... or "[[attachment]]"
author: 
published: 2026-09-01
project: "[[Project]]"     # optional
tags: [type/research, domain/market]
```

### `type/feedback`

```yaml
date: 2026-10-10
channel: support           # support · interview · review · nps · sales
customer: "[[Northwind Logistics]]"
person: "[[Jane Doe]]"     # optional
product_area: product/onboarding
sentiment: negative        # positive · neutral · negative
source: "ticket #4821"
tags: [type/feedback, domain/customers, product/onboarding]
```

### `type/person`

Structured data in frontmatter, narrative and interaction log in the body. **Work contact data only.** No personal identifiers, no private phone numbers, no health, family or financial information.

```yaml
tags: [type/person, crm/team]      # crm/* is the nature of the relationship
role: Head of Product
company: "[[Lumen Analytics]]"
works_at: "[[Lumen Analytics]]"    # typed edge
reports_to: "[[Ada Rossi]]"        # typed edge, team only
email: ben@example.com
linkedin: ben-okafor
location: Milan
last_contact: 2026-10-14           # external people
owner: "[[Ada Rossi]]"             # who holds the relationship, external people
up: "[[people]]"
```

### `type/company`

```yaml
tags: [type/company, crm/customer]
industry: logistics
stage: customer                    # prospect · customer · churned · partner · competitor
website: https://...
location: Bologna
owner: "[[Ben Okafor]]"            # account owner
customer_of: "[[Lumen Analytics]]" # typed edges: customer_of · partner_of · competitor_of · backed_by
since: 2025-03-01
up: "[[companies]]"
```

### `type/goal`

```yaml
status: active
period: 2026-Q4
owner: "[[Ada Rossi]]"
review_due: 2026-12-31
tags: [type/goal, domain/product]
```

### `type/playbook`, `type/policy`

```yaml
owner: "[[Person]]"
review_due: YYYY-MM-DD
last_verified: YYYY-MM-DD
applies_to: ["[[Team]]"]           # optional
tags: [type/playbook, domain/operations]
```

### `type/concept`

```yaml
tags: [type/concept, domain/product]
status: active                     # or disproven
up: "[[_MOC Product]]"
source: "[[Input note it was promoted from]]"   # when promoted
```

### `type/log` (Journal/Daily/)

File name `YYYY-MM-DD.md`. Sections: `## Notes`, `## Agents` (one line per automation run, written by the automation). No governance block.

### `type/automation`

```yaml
name: Weekly Review
description: ...
when: ["weekly Fri 16:00"]
mode: propose                      # report · propose · act
scope: ["Journal/Weekly/**"]       # globs the run may write, act mode only
agent: brain-curator               # optional: run this bundle instead of the body
cooldown: 6h
enabled: false
```

### `type/agent`

See the bundles in `_system/agents/`. Runtime fields: `autonomy` (`report · propose · act`), `read`, `write` (globs), `can_call`, `memory`, `soul`, `enabled`.

## Typed edges

Relationships as separate properties so each one is an edge in the graph and a column in a view:

| On | Properties |
|---|---|
| person | `works_at`, `reports_to`, `manages`, `owner` |
| company | `customer_of`, `partner_of`, `competitor_of`, `backed_by`, `owner` |
| decision | `decider`, `supersedes`, `project` |
| any input | `project`, `source` |

Reciprocity is best effort: when you add `reports_to` on a person, add `manages` on the manager if the note exists.
