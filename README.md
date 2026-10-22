# Company Brain template

A company brain is the shared, versioned, Markdown memory of an organization: what the company is, what it decided and why, who it works with, what it learned. People read it in Obsidian or any editor. AI agents (Claude Code, Exo inside Obsidian, Cowork, Codex) read it before they work and write back to it after, under rules that keep it true.

This repository is the **template**: the portable kernel plus an empty instance with a fictional sample company (Lumen Analytics) so the graph has something to show. The agent-side skills, hooks and health checks live in the [`company-brain` plugin](https://github.com/mariomile/company-brain).

## What you get

- **Ten folders** that tell an agent what a file *is*; tags say what it is *about*. Structure in [`_system/Brain Blueprint.md`](_system/Brain%20Blueprint.md).
- **Five living documents** in `Knowledge/Company/` (Company, Product, Customers, How We Work, Glossary), each with an owner and a review date.
- **A decision log** (`Decisions/`) with context, options, consequences, revisit conditions and dissent. Superseded, never deleted.
- **A CRM** of people and companies with typed relationships, current truth above and timeline below.
- **An agent layer** (`_system/`): kernel (`SOUL`, `ORG`, `NOW`), five rules, six specialist agents, six scheduled automations shipped off, Bases views, an append-only log.
- **Governance that is enforced, not hoped for:** `CODEOWNERS`, a PR template for knowledge changes, a CI health check, and a guard hook in the plugin that refuses root files, archive edits, synced-source edits and secrets.

## Setup (about 15 minutes)

1. **Use this template** on GitHub (or clone it) into a private repository of your organization. One brain per trust boundary: everyone with the repository sees everything in it.
2. **Install the plugin** in Claude Code:
   ```
   /plugin marketplace add mariomile/company-brain
   /plugin install company-brain@company-brain
   ```
   Or, in a terminal from the brain folder: `claude --plugin-dir /path/to/company-brain`.
3. **Open the folder** in Obsidian (optional but recommended): File → Open folder as vault. The config ships with Bases, daily notes and templates set up. Install `obsidian-git` for sync and, if you want the agent in the sidebar, `exo-agent` via BRAT.
4. **Run the onboarding interview** from the brain folder:
   ```
   claude
   /company-brain:onboard
   ```
   It asks one question at a time and fills `ORG.md`, `NOW.md`, the five living documents, the team and the current projects, then archives the sample notes.
5. **Fill `CODEOWNERS`** with the GitHub handles of the owners you just named, and turn on "Require review from Code Owners" on the main branch.
6. **Run the health check:** `/company-brain:health`. It should be green.

## Daily use

| When | Say or run |
|---|---|
| After a meeting | "minutes of today's product sync" → `/company-brain:meeting` |
| You decided something | "record the decision: we chose X over Y because Z" → `/company-brain:decide` |
| You have a document, a link, a thread | drop it in `_inbox/` and "triage the inbox" → `/company-brain:capture` |
| You need to know something | "what did we decide about pricing?" → `/company-brain:ask` |
| Monday morning | `/company-brain:brief` |
| Friday afternoon | `/company-brain:review` |
| A living document is due | `/company-brain:verify Product` |
| A new teammate | `/company-brain:onboard --teammate "Name"` |

Every answer cites its sources. If the brain does not know, it says so and proposes how to find out.

## How it grows and stays true

Capture → compile → query → promote → maintain → verify → review → measure. Who does what and how often is in the Blueprint, section 10. The short version:

- Agents write small, dated, sourced additions during work. Living documents are **proposed** to their owner, never rewritten by an agent.
- Automations climb an autonomy ladder (`report` → `propose` → `act`), one at a time, after two weeks of trusted output.
- The health check (`brain health`) runs on every pull request and every Monday: broken links, orphans, unregistered tags, stale living documents, root intrusions, secrets, rule cap, inbox age, `Input : Knowledge` ratio.
- The Friday review tells you what the brain learned, what is stale and whose it is, and proposes at most five changes.

## Language

The kernel is in English. Your content can be in any language: set `language` in `_system/brain.config.json` and agents follow it for new notes, and always match the language of the note they edit.

## License

MIT. Built on the Object-OS second-brain kernel by [Mario Miletta](https://marioverse.ai).
