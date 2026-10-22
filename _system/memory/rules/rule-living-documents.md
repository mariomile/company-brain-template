---
tags:
  - type/memory
rule: living-documents
created: {{today}}
---
# Rule: living documents

**Trigger:** you touch anything in `Knowledge/Company/`, `Resources/Playbooks/`, `Resources/Policies/`, a project note, a goal, or any note with `owner:` and `review_due:`.

A living document is a promise that its content is true today. The owner keeps the promise; you help without breaking it.

## What you may do without asking

- Add a dated fact line with its source.
- Update a fact with a dated trace: `<new> (since YYYY-MM-DD; before: <old>)`.
- Add wikilinks, fix a broken link, add a missing tag.
- Set `last_updated` and `last_edited_by`.

## What needs the owner

- Rewriting a section, changing a definition, removing a claim, changing a number without a source: **propose**, do not apply. In an interactive session, show the diff and ask. In a scheduled run, write the proposal to `_system/reports/proposals/YYYY-MM-DD <title>.md` with a ready-to-apply prompt.
- Changing `owner`, `review_due`, `confidentiality`, `audience`.
- A change to a policy: always a pull request reviewed by the owner in `CODEOWNERS`.

## Verification

- Never set `last_verified` yourself. Only the owner verifies, in the `verify` flow: they confirm the content, you set `last_verified` to today and `review_due` to today plus the cadence in `object-schema.md`.
- A document past `review_due` is **stale**: say so in one line when you cite it, and keep using it (stale is not false).
- A document past twice its cadence: the weekly review proposes `status: paused` and names the owner. Never silently.

## Why

Wikis rot because nobody owns the page. Here, every living document has one owner and one date, the health check lists what is past due, and the brief shows it until it is verified.
