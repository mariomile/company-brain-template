---
tags:
  - type/reference
owner: "[[{{owner-brain}}]]"
review_due: {{review-date}}
confidentiality: internal
last_updated: {{today}}
---
# Tag registry

> The official registry of tags in this brain. Search, tags and the graph are how people and agents navigate. Every note has 1 to 4 tags. A tag not listed here is unregistered: the health check counts it, the librarian proposes it for registration or replacement.
>
> Adding a namespace or a `type/*` value is a decision (`Decisions/`), not an edit. Adding a `domain/*` value is an edit by the brain owner, recorded here with the date.

## Quick reference

```yaml
status: active            # property, not a tag
tags:
  - type/<kind>           # ALWAYS: what the file is
  - domain/<area>         # if applicable: what it is about
  - <namespace>/<sub>     # optional tier 2
```

## Tier 1: `#type/*` (universal, always present)

Inferred from the folder, but always written in the tags so views and search work without paths.

| Tag | Meaning | Where it lives |
|---|---|---|
| `type/note` | quick note, no other type fits | anywhere |
| `type/log` | daily log | `Journal/Daily/` |
| `type/review` | weekly review note | `Journal/Weekly/` |
| `type/meeting` | minutes of one meeting | `Input/Meetings/` |
| `type/transcript` | synced transcript, read-only | `Input/Meetings/<sync>/` |
| `type/conversation` | summary of an email, chat or ticket thread | `Input/Conversations/` |
| `type/document` | external document ingested | `Input/Documents/` |
| `type/research` | article, report, interview, competitor note | `Input/Research/` |
| `type/feedback` | customer feedback, review, support theme | `Input/Feedback/` |
| `type/concept` | atomic permanent concept | `Knowledge/<Domain>/` |
| `type/living` | living document of the company | `Knowledge/Company/` |
| `type/glossary` | the glossary | `Knowledge/Company/Glossary.md` |
| `type/index` | navigable index, including MOCs (`_MOC <Domain>.md`) | `_system/indices/`, `Knowledge/**/_MOC *.md` |
| `type/person` | a person | `CRM/People/` |
| `type/company` | an organization: customer, partner, investor, competitor | `CRM/Companies/` |
| `type/decision` | decision record | `Decisions/` |
| `type/project` | project note | `Active/Projects/<Name>/<Name>.md` |
| `type/goal` | goal, OKR, target | `Active/Goals/` |
| `type/task` | a unit of execution with its own note (rare; most tasks are checkboxes in the project note) | `Active/Projects/<Name>/` |
| `type/output` | finished deliverable, wherever it lives | `Output/`, `Active/Projects/*/` |
| `type/template` | note template | `_system/templates/` |
| `type/playbook` | how we do a recurring thing | `Resources/Playbooks/` |
| `type/policy` | a rule of the company | `Resources/Policies/` |
| `type/memory` | open loops and their record | `_system/memory/` |
| `type/automation` | scheduled run definition | `_system/automations/` |
| `type/report` | what an automation wrote | `_system/reports/` |
| `type/reference` | system reference and contracts | `_system/` |
| `type/context` | map or scope context | `_system/brain-context.md` |

**`#type/output` is both a folder and a tag.** `Output/` is the home of deliverables with no project home. A deliverable that belongs in its project stays there and carries the tag. The single view composes: `inFolder("Output") OR hasTag("type/output")`.

**MOC rule.** A domain in `Knowledge/` over ~50 notes requires a `_MOC <Domain>.md` with `#type/index`. Count with the plugin: `brain health` reports domains over the threshold.

## Tier 1: `#domain/*` (what it is about, cross-folder)

The namespace is kernel; the values are yours. Keep the set finite and orthogonal: 6 to 12 values. Start from the folders of `Knowledge/` and add only when a theme keeps appearing across folders without a home.

| Tag | Scope | Added |
|---|---|---|
| `domain/product` | the product: features, roadmap, specs, metrics | {{today}} |
| `domain/customers` | who buys, why, how they use it; segments, accounts | {{today}} |
| `domain/market` | competitors, positioning, pricing, industry | {{today}} |
| `domain/engineering` | architecture, stack, delivery, incidents | {{today}} |
| `domain/operations` | processes, finance, legal, hiring, tooling | {{today}} |
| `domain/people` | team, roles, culture, ways of working | {{today}} |
| `domain/knowledge` | this brain itself: structure, rules, agents | {{today}} |

## Tier 2: optional sub-categorization

| Namespace | Values | On which notes |
|---|---|---|
| `crm/*` | `team · customer · prospect · partner · investor · advisor · vendor · competitor · other` | people and companies: the nature of the relationship |
| `customer/*` | your segments, for example `customer/enterprise`, `customer/smb` | feedback, companies, research |
| `product/*` | your product areas, for example `product/onboarding`, `product/billing` | concepts, decisions, feedback, projects |

Tier 2 namespaces beyond these three are a decision.

## Forbidden

Tried and removed in the reference vault. Do not reintroduce.

| Namespace | Why |
|---|---|
| `#stage/*` | redundant with `type/*` plus folder |
| `#status/*` | duplicates the `status:` property |
| `#input` `#output` `#knowledge` as tags | the folder says it |
| `#client/<name>`, `#project/<name>`, `#person/<name>` | entities are notes to link, not tags. Use `[[wikilinks]]` and the `project:` property |
| `#urgent`, `#todo`, `#important` | state and priority are properties or checkboxes, not tags |

## History

- {{today}}: registry created from the kernel. No instance values yet beyond the default domains.
