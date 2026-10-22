---
tags:
  - type/living
  - domain/customers
owner: "[[{{owner-customers}}]]"
review_due: {{review-date}}
last_verified: {{today}}
confidentiality: confidential
up: "[[Company]]"
last_updated: {{today}}
---
# Customers

> Who buys, why, how they use the product, and what they tell us. Accounts are in `CRM/Companies/`; feedback in `Input/Feedback/`; this is the synthesis. What they use is in [[Product]].

## Now

*Current facts as dated lines with a source: number of customers or accounts, the ideal customer profile in one line, the top reason customers leave or never start. Source: the billing export, the CRM, sales and support calls.*

- 

## Segments

*Who buys, one row per segment: the role, the company size, the trigger that makes them look for us, what they need. Give each segment a tag `customer/<segment>`. Source: sales calls, the CRM.*

| Segment | Tag | Who | What they need |
|---|---|---|---|
| {{segment}} | `customer/{{segment-tag}}` | {{who}} | {{need}} |

## What they say

*The themes from feedback, support and interviews, each linking to its notes. Source: `Input/Feedback/`, support tickets, customer interviews. Once feedback passes 50 notes, themes move to `Knowledge/Customers/` with a `_MOC Customers`; until then the feedback view is `_system/views/feedback.base`.*

## Timeline

*Dated changes in who the customers are: first customer, new segment, notable wins and losses. Source: the CRM, the founders.*

- {{today}}: created from the template.
