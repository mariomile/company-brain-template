# Company Brain template

A company brain is the shared, versioned, Markdown memory of an organization: what the company is, what it decided and why, who it works with, what it learned. People read it in Obsidian or any editor. AI agents (Claude Code, Cowork, Exo inside Obsidian, Codex) read it before they work and write back to it after, under rules that keep it true.

This repository is the **template**: the structure, the contracts and the agent layer, with the company documents left as skeletons to fill and a few notes of a fictional company (Lumen Analytics, each marked `sample: true`) so the graph has something to show. The agent side (skills, hooks, the `brain` script) is the [`company-brain` plugin](https://github.com/mariomile/company-brain).

## What you get

- **Ten folders** that tell an agent what a file *is*; tags say what it is *about*. Structure and reasons in [`_system/Brain Blueprint.md`](_system/Brain%20Blueprint.md).
- **Five living documents** in `Knowledge/Company/` (Company, Product, Customers, How We Work, Glossary), each with an owner and a review date.
- **A decision log** (`Decisions/`): context, options, consequences, when to revisit, dissent. Superseded, never deleted.
- **A CRM** of people and companies with typed relationships, current truth above and timeline below.
- **An agent layer** (`_system/`): the kernel (`SOUL`, `ORG`, `NOW`), five rules, six scheduled automations shipped off, connected sources, Bases views, an append-only log.
- **Governance that is enforced, not hoped for:** a guard hook that refuses root files, archive edits, edits to synced sources and secrets; a CI health check; `CODEOWNERS` for the documents that change how the company works.

## Setup

You need [Claude Code](https://code.claude.com) and [Node.js](https://nodejs.org) 18 or newer on every machine that works on the brain: the plugin's guard and checks run on Node, and without it they are switched off.

1. **Get the template.** To share it with the team: **Use this template** on GitHub into a private repository of your organization, then clone it. To keep it on your machine for now: clone it, delete `.git`, `git init`. One brain per trust boundary: everyone with the repository sees everything in it.
2. **Open the folder in Claude Code.** Its `.claude/settings.json` offers the plugin on first open: accept. Or install it by hand:
   ```
   /plugin marketplace add mariomile/company-brain
   /plugin install company-brain@company-brain
   ```
3. **Run `/company-brain:setup`.** It walks every step and skips what is done, so you can stop and run it again:
   - where the brain lives: on this machine or on GitHub;
   - the company: it drafts `ORG.md`, `NOW.md`, the five living documents, the team, the projects and the decisions from your material (a website, a deck, a docs folder, an export, a whole vault), archives the sample notes, then asks you to confirm or fix about ten things;
   - the input sources, the meeting recorder (Granola or yours) first, with a first pull so you see it work;
   - the routines, the morning brief first, run once with you and then scheduled;
   - the owners in `CODEOWNERS`, if the brain is on GitHub;
   - a health check with no errors.

   `brain setup` prints the same checklist at any time.
4. **Optional:** open the folder in Obsidian (File, Open folder as vault: Bases, daily notes and templates are set up).

## Daily use

| When | Say or run |
|---|---|
| After a meeting | "minutes of today's product sync", or drop the transcript in `_inbox/` → `/company-brain:meeting` |
| You decided something | "record the decision: we chose X over Y because Z" → `/company-brain:decide` |
| You have a document, a link, a thread | drop it in `_inbox/` and "triage the inbox" → `/company-brain:capture` |
| You need to know something | "what did we decide about pricing?" → `/company-brain:ask` |
| Pull from Slack, Drive, Notion, the meeting recorder | "ingest" → `/company-brain:ingest` (sources in `_system/sources.md`) |
| Monday morning | `/company-brain:brief` |
| Friday afternoon | `/company-brain:review` |
| A living document is due | "verify Product" → `/company-brain:governance` |
| A new teammate | "onboard Marta, she joins sales" → `/company-brain:onboard` |

Every answer cites its sources. If the brain does not know, it says so and proposes how to find out.

## Working together

A brain that lives on one machine has one lane: `brain sync` commits there and pushes nothing. On GitHub, two lanes:

- **Day-to-day knowledge goes straight to main.** Minutes, inputs, proposed decisions, CRM, project notes, the journal. The agent runs `brain sync` after it writes: pull, commit, push. Nobody waits for a review to save a meeting.
- **What changes how the company works goes through a pull request** reviewed by its owner: the living documents, policies, playbooks and the brain's own contracts (`CODEOWNERS` lists them). Agents never rewrite these; they propose.

The guard hook checks every write an agent makes with its file tools. It does not see shell commands, so it protects against mistakes, not against someone determined to get around it. The CI health check is the second line.

## Scheduled routines

The automations in `_system/automations/` (the morning brief, inbox triage, meeting minutes, ingest, the weekly review, the librarian) ship off. Each runs only when its file says `enabled: true`; `setup` turns the first one on with you.

- **Brain on your machine:** `brain routine <name>` runs one with Claude Code, checks it stayed inside its scope and commits locally. `brain routine <name> --cron` prints the crontab line that schedules it; the machine must be on at that time.
- **Brain on GitHub:** `.github/workflows/brain-routines.yml` runs them with Claude Code. Reports land on a rolling issue; proposals and changes arrive as a pull request for their owners. It needs the `ANTHROPIC_API_KEY` secret (or `CLAUDE_CODE_OAUTH_TOKEN`) and Actions allowed to create pull requests. Run each one once by hand from the Actions tab before trusting the schedule.

## How it grows and stays true

Ingest → capture → compile → query → promote → maintain → verify → review → measure. Who does what and how often is in the Blueprint, section 10. The short version:

- Agents write small, dated, sourced additions during work. Living documents are **proposed** to their owner, never rewritten by an agent.
- Automations climb an autonomy ladder (`report` → `propose` → `act`), one at a time, after two weeks of trusted output.
- The health check (`brain health`) runs on every pull request and every Monday: broken links, orphans, unregistered tags, stale living documents, root intrusions, secrets, rule cap, `Input : Knowledge` ratio.
- `brain metrics` counts what the brain did this week, including the questions it answered and the ones it could not: those say what to write next.

## Language

The kernel is in English. Your content can be in any language: set `language` in `_system/brain.config.json` and agents follow it for new notes, and always match the language of the note they edit.

## License

MIT. Built on the Object-OS second-brain kernel by [Mario Miletta](https://marioverse.ai).
