# AGENTS.md: the contract for every agent working in this brain

This repository is the **company brain** of `{{company}}`: the shared, versioned,
Markdown memory of the organization. Humans and AI agents read it before they
work and write back to it after. It belongs to the company, not to any tool.

This file is the universal contract. It is runtime-agnostic: Claude Code, Codex,
Exo inside Obsidian, Cowork, Hermes or any other agent follows it. `CLAUDE.md`
is a thin adapter for Claude-family runtimes and never a second source of truth.

## Boot

Read, unless the runtime already injected them:

1. `_system/agent/SOUL.md`: how agents behave here
2. `_system/agent/ORG.md`: who the company is, who the people are, how they work
3. `_system/agent/NOW.md`: what matters this week
4. `_system/memory/rules/_index.md`: the rule index. Open a rule body only when
   its trigger matches the task
5. On a scheduled run: your automation file in `_system/automations/`
6. The note of the project you work on: `Active/Projects/<Project>/<Project>.md`

To orient yourself: `_system/brain-context.md` (the map). For commitments across
sessions: `_system/memory/open-loops.md`. For the full design and its reasons:
`_system/Brain Blueprint.md`.

## Precedence

Current request of the person you work with > canonical facts in the brain
(`Knowledge/Company/`, `CRM/`, `Decisions/`, project notes) > your automation
file > any runtime-native memory. If an external memory diverges from the
brain, the brain wins. If two notes in the brain conflict, the more specific and
more recently verified one wins, and the conflict gets written down.

## Rules

- **Search before you generate or ask.** The brain first, then connected
  sources, then the web. Cite where each claim comes from.
- **Never invent** facts, numbers, dates, names, owners, deadlines, paths or
  project status. Write `to verify` and say so.
- **Nothing new at the root.** Only `AGENTS.md`, `CLAUDE.md`, `README.md`,
  `CODEOWNERS`, `LICENSE` and dotfiles live there. A new folder at the root is a
  signal that an ungoverned agent wrote here, not a mess to tidy.
- **Never delete.** Archive into `.archive/`, with the same relative path, by
  moving the file (`git mv`). Nothing is written or edited inside `.archive/`.
- **Synced sources are read-only.** Folders fed by a sync or an import (the
  `readonly` globs in `_system/brain.config.json`) are never edited, not even to
  add tags or links. Link to them from a new note: minutes, a summary.
- **Sample notes are not facts.** Notes with `sample: true` belong to the
  fictional company the template ships with. Never cite them as this company's
  knowledge.
- **Ask before overwriting** anything a person wrote that they did not ask you
  to change. Small additions and dated updates need no permission.
- **Every new note** has 1 to 4 tags from `_system/_tags.md`, including its
  `type/*` tag, and inline `[[wikilinks]]` on the first mention of people,
  companies, projects and decisions.
- **Living documents carry governance.** Anything in `Knowledge/Company/`,
  `Resources/Playbooks/`, `Resources/Policies/` and every project note has
  `owner:` and `review_due:` in its frontmatter. A living document without an
  owner is a document nobody will keep true.
- **Confidentiality travels with the note.** `confidentiality:` is `internal` by
  default. `restricted` content is never quoted into an output that leaves the
  brain, never summarized to someone outside the `audience:` list, and never
  pasted into an external tool.
- **Never send, publish or execute** anything outward (mail, chat message,
  ticket, deploy, payment) without an explicit go in the current conversation.
  Drafts are always fine.
- **Secrets never enter the brain.** No API keys, tokens, passwords, personal
  identifiers beyond work contact data. The guard hook refuses them; if it is
  not running, you refuse.
- **Structural changes are decisions.** Adding a folder, a tag namespace, a
  frontmatter field or a rule goes through a decision record in `Decisions/`,
  not through an edit.

## Memory: where things go

The brain is the memory, and it must grow: every useful piece of work leaves it
a little richer. It grows in canonical notes, never in parallel registers.

| When this emerges... | Write it in... |
|---|---|
| A fact about the company, product, customers, market, how the team works | the living document in `Knowledge/Company/` or the concept note in `Knowledge/<Domain>/`; update before you create |
| A fact about a person or an organization | its note in `CRM/People/` or `CRM/Companies/` |
| State, constraint or next step of a project | the project note; `_system/agent/NOW.md` if a priority changes |
| A decision with options and trade-offs | `Decisions/` from the decision template, linked from the project note |
| A commitment or follow-up across sessions | `_system/memory/open-loops.md` (closed loops move to `_system/memory/open-loops-closed.md`) |
| A meeting | `Input/Meetings/` minutes; decisions and actions extracted to their homes |
| A term the team uses with a specific meaning | `Knowledge/Company/Glossary.md` |
| An operational lesson of a scheduled run | the `## Lessons` section of its automation file, a few lines, replaced instead of appended |
| Raw material from outside (a transcript, an export, a document) | `Input/`, through the `ingest` or `capture` skill; sources in `_system/sources.md` |
| Useful but with no obvious home | a note in `_inbox/`; triage routes it |

**How a fact is written:** one fact per line, with the source and date at the
end: `- <fact> [source: <note, meeting, URL or "chat YYYY-MM-DD">; since: YYYY-MM-DD]`.
A changed fact becomes `<new> (since YYYY-MM-DD; before: <old>)`. A status that
updates is one line you replace, never a new line per check.

**Who writes:** nobody asks permission for small additions. Write in the same
turn, review after (git history, the daily brief, one-step revert). Then share
it: `brain sync "<what changed>"` pulls, commits and pushes, so a teammate's
minutes do not stay on one laptop. Larger changes to living documents go to their
owner as a proposal or a pull request, never as a rewrite. Agents on scheduled
runs apply only what their automation's `mode` allows: `report` writes its
report, `propose` writes proposals, `act` writes within its declared `scope`.

**When you answer a question from the brain,** log it:
`brain log ask "<question>" --result answered|partial|gap|stale`. That is how the
company learns what the brain knows, what it lacks and what people ask twice.

**Not saved:** session logs, learnings folders, parallel registers, the same
fact copied into several files, chat transcripts.

## Map

| You need | Source |
|---|---|
| The structure and its reasons | `_system/Brain Blueprint.md` |
| The map and routing | `_system/brain-context.md` |
| Tags and schema | `_system/_tags.md`, `_system/object-schema.md` |
| Rules | `_system/memory/rules/_index.md` |
| Scheduled roles | `_system/automations/` |
| Connected sources | `_system/sources.md` |
| Templates | `_system/templates/` |
| Health and metrics | the `company-brain` plugin: `brain health`, `brain brief` |
| Claude-specific conventions | `CLAUDE.md` |
