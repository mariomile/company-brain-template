---
tags:
  - type/reference
owner: "[[{{owner-brain}}]]"
review_due: {{review-date}}
---
# Sources

> Where the brain gets material from outside, and how far each source has been read. The `ingest` skill and automation read this table: a source not listed here is never pulled. Adding a source is an edit by the brain owner; an agent only updates `last_sync`.

| Source | Kind | Connector | Destination | Audience | Owner | Status | Last sync |
|---|---|---|---|---|---|---|---|
| Meeting recorder | meetings | Granola (sync or MCP) | `Input/Meetings/Granola/` | internal | {{owner-brain}} | paused | |
| Team chat | conversations | Slack MCP, channels listed below | `Input/Conversations/Raw/` | internal | {{owner-brain}} | paused | |
| Shared drive | documents | Google Drive MCP, folders listed below | `Input/Documents/Raw/` | internal | {{owner-brain}} | paused | |
| Wiki | documents | Notion MCP, pages listed below | `Input/Documents/Raw/` | internal | {{owner-brain}} | paused | |
| Support | feedback | helpdesk MCP or export | `Input/Feedback/Raw/` | internal | {{owner-brain}} | paused | |

**Kinds:** `meetings` go to minutes (`company-brain:meeting`), everything else to triage (`company-brain:capture`). **Status:** `active` sources are pulled by the ingest run; `paused` ones are not. **Last sync:** `YYYY-MM-DD HH:MM`, written by the agent after a successful pull.

## Scope per source

What exactly to read, so nobody pulls the whole company into the brain.

- **Team chat:** channels: {{channels}}. Never direct messages.
- **Shared drive:** folders: {{folders}}.
- **Wiki:** pages and their children: {{pages}}.

## One-time imports

An export (Notion, Confluence, a Drive folder) dropped once: unzip it under `_inbox/import-YYYY-MM-DD/` and run `company-brain:ingest` with "import". It is processed in batches and never re-imported.
