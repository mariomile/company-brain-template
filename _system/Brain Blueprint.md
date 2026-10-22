---
tags:
  - type/reference
  - domain/knowledge
owner: "[[{{owner-brain}}]]"
review_due: {{review-date}}
confidentiality: internal
status: active
up: "[[brain-context]]"
related:
  - "[[_tags]]"
  - "[[object-schema]]"
  - "[[brain-context]]"
aliases:
  - Company Brain Blueprint
  - Brain Kernel
---
# Brain Blueprint

> **What this is.** The canonical specification of this company brain: a shared memory that a person and a fleet of AI agents operate with the same effectiveness. It describes a **portable kernel** (sections 1 to 7), identical for every company, and the **instance** (section 8), which is yours.
>
> **Who reads it.** A person setting up or changing the brain. An agent reads `AGENTS.md` and the contracts (`_tags.md`, `object-schema.md`, the rules); it opens this file only when a structural question comes up.

---

## 1. Five principles

Everything else follows from these. If a rule below looks arbitrary, its reason is here.

**1. The folder says what a file IS. The tag says what it is ABOUT.**
There is no `Pricing/` folder. A note about pricing lives in `Knowledge/Product/` if it is a permanent concept, in `Decisions/` if it is a choice, in `Active/Projects/` if it is live work, and in all three cases it carries `#domain/product`. Cross-cutting views are composed at query time (search, Bases, tags), never by moving files.

**2. The folder encodes what does not change. Tags and properties encode what does.**
The nature of a file is stable for its whole life: minutes never become a playbook, a template never becomes a deliverable. Its *state* changes all the time. So `status` is a property, not a tag and not a folder. Any axis that evolves (stage, priority, review state) cannot be a folder, because it would force moving files, which breaks links, sync and automations.

**3. The value is in the graph, not in the archive.**
A system of record returns what you put in; a knowledge graph composes value at every connection. Folders only answer "where do I write this?". The return comes from links. A note without links is inert, however well filed.

**4. The path is free semantics for an agent.**
For an agent, a file's location is a retrieval scope, a permission boundary and a type, inferred without opening the file. Sharp boundaries mean shorter rules, fewer tokens, less ambiguity. An ambiguous structure costs every session, forever.

**5. The structure serves decisions, not completeness.**
The metric is *better decisions per token*, not the number of notes. Every rule here exists because it saves an error or a context recovery.

**Company corollary: a document without an owner is a document nobody keeps true.** A personal brain has one author. A company brain has many, and the main risk is not accumulation but *drift* between the documents and the reality of the product. So living documents carry an owner and a review date, and the brain measures its own staleness.

---

## 2. The structure: ten top-level folders

```
_inbox/       Raw capture, not yet processed. Trends to zero.
Input/        External or raw material: meetings, conversations, documents, research, feedback
Knowledge/    Permanent, refined knowledge, by domain. Knowledge/Company/ holds the living documents
CRM/          Relationships: people and organizations
Decisions/    The decision log: context, options, choice, consequences, review
Active/       Work in progress with an outcome: projects and goals
Output/       What the company produces and delivers
Journal/      The time trace: daily and weekly team log
Resources/    Reusable tools: templates, playbooks, policies, attachments
_system/      The machine layer: agent kernel, memory, rules, views, automations
.archive/     History. Never delete, always archive.
```

The flow of knowledge work reads in the order of the folders:

```
_inbox ──► Input ──► Knowledge ──► Output
              │          ▲            ▲
              └──────────┼────────────┘
                      Active  (the engine that consumes and produces)
                    Decisions  (the why, extracted from everything)
                     Journal  (the trace of what happened)
```

**A note does not migrate along this chain.** Promotion **creates a new note** in the next stage and leaves the original where it is, linked. Minutes in `Input/Meetings/` that produce a decision stay in `Input/`; the decision is a new note in `Decisions/` with `source:` pointing back. This is what makes the chain compatible with Principle 2.

### The contract of each folder

Normative table: an agent decides where to write by reading only this.

| Folder | Contains | Does NOT contain | Who writes |
|---|---|---|---|
| `_inbox/` | unclassified capture, dropped files, clips | anything already classifiable | people, clippers, agents routing from chat |
| `Input/Meetings/` | one note per meeting: minutes, decisions, open questions. Synced transcripts in a read-only subfolder | notes you wrote yourself | agents (meeting skill), sync plugins |
| `Input/Conversations/` | summaries of email, chat and ticket threads that contain decisions or commitments | raw text, logistics-only threads | agents |
| `Input/Documents/` | external documents ingested: contracts, briefs, specs received, PDFs as notes | deliverables of the company | agents (capture skill), people |
| `Input/Research/` | articles, reports, competitor notes, interviews with users | opinions of the team | agents, people |
| `Input/Feedback/` | customer feedback, support themes, reviews, NPS verbatims | triaged product knowledge | agents, syncs |
| `Knowledge/Company/` | the living documents: company, product, customers, how we work, glossary | project state, meeting notes | owners, agents by proposal |
| `Knowledge/<Domain>/` | atomic permanent concepts, MOC | notes about people or organizations, ephemeral notes | people and agents, with review |
| `CRM/People/`, `CRM/Companies/` | team members, customers, partners, investors, competitors | concepts, project notes | agents and people |
| `Decisions/` | decision records with options and trade-offs | opinions, open questions (those are `Input/` or project notes) | the decider, written by anyone |
| `Active/Projects/<Name>/` | the project note plus its working files | permanent reference, consumed material | people and agents |
| `Active/Goals/` | OKRs, targets, north star | tasks | leadership, agents by proposal |
| `Output/` | deliverables without a project home; `_artifacts/` for self-contained HTML | drafts, work in progress | agents, people |
| `Journal/Daily/` | the team's daily log: what happened, agent lines | permanent content (promote it) | people and agents |
| `Journal/Weekly/` | the weekly review note | — | the review automation |
| `Resources/Templates/` | note templates for people | — | the brain owner |
| `Resources/Playbooks/` | how we do recurring things: runbooks, procedures | policies | process owners |
| `Resources/Policies/` | rules of the company: security, expenses, communication | procedures | leadership |
| `_system/` | agent kernel, memory, rules, indices, views, automations, templates for agents | human reading material | agents, the brain owner |
| `.archive/` | everything inactive, same relative path | — | move only, never edit |

---

## 3. Tags and properties

```yaml
---
tags:
  - type/<kind>        # ALWAYS. What the file is.
  - domain/<area>      # when applicable. What it is about.
  - <tier2>/<sub>      # optional: crm/*, product/*, customer/*
status: active         # PROPERTY, never a tag. Only where a lifecycle makes sense
---
```

**At most 4 tags per note.** More tags means less signal per tag.

**Two live namespaces, and only two.**

- **`#type/*`**: the universal axis, always present. The full set is in `_tags.md`.
- **`#domain/*`**: the thematic axis, cross-folder. The values are yours (section 8).

**Status is a property, never a tag.** Values: `active · backlog · done · draft · paused · archived`, plus `superseded` (decisions) and `disproven` (concepts, references).

**Forbidden namespaces**, each tried and removed in the reference vault, not theorized:

| Forbidden | Why it failed |
|---|---|
| `#stage/*` | fleeting/literature/evergreen was redundant with `type/*` plus the folder |
| `#status/*` | duplicated the `status:` property |
| `#input/#output/#knowledge` | the folder already says it |
| `#client/<name>`, `#project/<name>` | an entity is a note to link, not a tag to spray. Use `[[wikilinks]]` and the `project:` property |

---

## 4. Governance properties

This is the one structural addition a company brain makes to a personal one.

| Property | On which notes | Values | Why |
|---|---|---|---|
| `owner` | every living document, project note, playbook, policy | `"[[Person]]"` | the person accountable for the note being true |
| `review_due` | same | `YYYY-MM-DD` | the date after which the note is stale until re-verified. Default cadence per type in `object-schema.md` |
| `last_verified` | same | `YYYY-MM-DD` | when the owner last confirmed the content. Set when re-verifying; bump `review_due` by the cadence |
| `confidentiality` | any note; default `internal` if absent | `public · internal · confidential · restricted` | what the note may be quoted into. See the policy below |
| `audience` | `restricted` notes | list of `"[[Person]]"` or role names | who may see the content |
| `source` | inputs, decisions, facts derived from somewhere | `"[[note]]"` or URL or `chat YYYY-MM-DD` | provenance. A fact without a source is an opinion |
| `project` | meetings, conversations, decisions, feedback | `"[[Project]]"` or `none` or `to verify` | the dossier that must find this note |

**Confidentiality policy.**

- `public`: may be quoted anywhere, including outside the company.
- `internal` (default): any teammate with access to the repository. May be quoted in internal outputs.
- `confidential`: still in the repo, but never quoted verbatim into external outputs (proposals, posts, support answers). Summaries only, and the note says so.
- `restricted`: in the repo only if the repository itself has that trust level; otherwise it belongs in a separate brain. Agents do not summarize it to anyone not in `audience:` and never copy it into another note.

**The repository is the access boundary.** Git cannot hide a folder from someone who has the repo. If a group of people must not see a class of content, that content lives in a second brain with its own access, and this brain links to it by name only. One brain per trust boundary.

**Owner cadence.** When a living document passes `review_due`, the health check lists it, the weekly review assigns it to the owner, and the daily brief shows it until it is verified. A note stale for more than twice its cadence is marked `status: paused` by the review proposal, never silently.

---

## 5. Graph rules

- **Wikilinks, never markdown links**, for any internal reference. Wikilinks survive renames.
- **Every note has at least 2 outgoing links.** Fewer is an orphan: it exists but does not compose. Agents add links proactively.
- **Two graph properties**, counted as links by the views:
  ```yaml
  up: "[[Parent note or MOC]]"      # quotes required
  related: ["[[Peer note]]"]
  ```
- **MOCs are first-class.** A *Map of Content* (`_MOC <Domain>.md`, tag `#type/index`) is a hub note that indexes a domain by theme. **Operating rule: a domain over ~50 notes requires a MOC.** This is where most knowledge bases fail: they accumulate without building the maps.
- **Unlinked mentions:** when a note names an existing entity without linking it, propose the wikilink. This is the ordinary maintenance of the graph.
- **Typed edges on CRM notes** (`works_at`, `reports_to`, `customer_of`, `partner_of`, `competitor_of`, `decided`) are separate frontmatter properties so each one counts as an edge and is queryable.

**The diagnostic ratio.** `Input : Knowledge` measures the health of the system. Above ~2:1 the brain is ingesting more than it distills, and the bottleneck is **not** capture: it is promotion. Any intervention that adds inputs while the ratio is high works on the wrong side of the pipe.

---

## 6. The agentic layer: `_system/`

What distinguishes an *agentic* company brain from a well-ordered wiki: the memory that survives the session, and the rules that let many agents and people write to the same files without stepping on each other.

```
_system/
├── agent/            shared kernel: SOUL.md · ORG.md · NOW.md
├── agents/           complete bundles: <slug>/SOUL.md · AGENT.md
├── memory/
│   ├── rules/        approved behaviors (max 8), loaded just-in-time
│   ├── agents/       dedicated memory per agent, a few lines each
│   ├── inbox/        transit of automatic memory, emptied by consolidation
│   └── open-loops.md commitments across sessions
├── indices/          navigable indices: projects, domains, people
├── views/            .base files: the query layer over everything else
├── automations/      scheduled runs: when, mode, scope, prompt
├── templates/        templates agents use
├── reports/          what automations wrote: briefs, reviews, health
└── _tags.md · object-schema.md · brain-context.md · Brain Blueprint.md   ← the contracts
```

Two natures live here, keep them separate in your head:

- **State that changes**: `memory/`, `indices/`, `reports/`, `agent/NOW.md`. Changes follow declared ownership and scope.
- **Contracts that do not change**: `_tags.md`, `object-schema.md`, this file, `AGENTS.md`. Changing one is a **decision** in `Decisions/`, not an edit.

**Memory routing:**

```text
verified work
  ├── current state ........ NOW.md / project note / living document
  ├── open commitment ...... open-loops.md
  ├── choice ............... Decisions/
  ├── relationship ......... CRM/
  └── knowledge ............ the canonical note in Knowledge/
```

The memory grows in canonical notes. Agents capture during work (add, update with a dated trace, or ignore), the consolidation run empties the transit and deduplicates, the brief shows what was written. No parallel register. Rules are born only with a decision and within the cap of 8.

### Autonomy ladder

Every automation and every agent declares a `mode`. The ladder is climbed one step at a time, per automation, after its output has been trusted for a few runs:

| Mode | Writes | When to use |
|---|---|---|
| `report` | nothing in the brain; a report in `_system/reports/` | first weeks of any automation; briefs |
| `propose` | proposals with ready-to-apply prompts, in `_system/reports/` | reviews, triage with ambiguity |
| `act` | within its declared `scope:` globs only, with a commit per run | triage, indices, consolidation, meeting minutes |

An automation in `act` mode never touches a living document's body: it proposes. The guard hook enforces `scope:` when the runtime passes it.

### Multi-agent, multi-person: the brain belongs to no tool

1. **The universal contract is `AGENTS.md`.** `CLAUDE.md` is a short adapter, never a second source of truth.
2. **Common boot, progressive loading.** An agent with pre-injected context verifies what it already received; a cold agent reads `AGENTS.md` → kernel → rule index → bundle → project note.
3. **Root guard.** Nothing new at the root, ever. A folder that appears at the root is a signal of intrusion: an agent without the rules wrote the generic default (`notes/`, `docs/`, `output/`). Find out who wrote it before deciding what to do with the content.
4. **Precedence on conflicts:** current request → `AGENTS.md` and applicable rules → shared kernel → specialist contract → canonical memory → agent memory → runtime memory.
5. **Concurrency.** Agents write small, additive, dated changes and commit per run. Two agents never run in `act` mode on overlapping `scope:` at the same time. Living documents change by pull request; `merge=union` in `.gitattributes` keeps both sides of a conflict for the owner to resolve.

### Complete agents and adapters

An agent is a bundle `_system/agents/<slug>/` with `SOUL.md` and `AGENT.md`, plus `_system/memory/agents/<slug>.md`. Adapters in `.claude/agents/` (if any) only point the runtime at the bundle. Exo reads the bundle directly.

### Contracts per scope

Every project has a **project note** named like the project (`Active/Projects/<Name>/<Name>.md`): its card and the working memory of agents. Read before working on the project, updated after. A project without an updated note is a project an agent will reason about badly, with confidence, which is worse.

---

## 7. Anti-patterns

Errors actually paid for, not hypotheses.

| Anti-pattern | Why it fails |
|---|---|
| Folders per stage (`Drafts/`, `Final/`) | stage changes → files move → paths, syncs, views break. Use `status:` |
| Folders per domain everywhere | domain is multiple and changes. It is a tag. (Declared exception: `Knowledge/`) |
| The same axis as tag *and* folder | double encoding, double maintenance, guaranteed drift |
| Status tags | pollutes the graph with historical noise. Property |
| Reorganizing instead of synthesizing | moving folders *looks like* knowledge work. It is container work. If `Input:Knowledge` is high, structure is not the problem |
| New containers without removing any | every top-level folder is one more decision at every capture |
| Notes without tags | invisible to tag search, views and graph. They stop compounding |
| Living documents without owner | nobody notices when they drift from reality. The wiki rots in six months |
| Review dates nobody checks | a date in frontmatter is a promise; the health check and the brief are what keep it |
| Bulk frontmatter mutation via a YAML parser | parsers break unquoted wikilinks. Insert raw lines, on a versioned repo |
| Counting tags with `grep` | it counts textual mentions too. Use the plugin script, which separates frontmatter from body |
| A second source of truth (a wiki, a Notion, an agent memory store) | drift is guaranteed within weeks. The brain is the source; everything else is a cache or a view |
| Secrets in notes "just for now" | the repo is cloned on every laptop and read by every agent |

---

## 8. Kernel vs instance: what is portable

| Element | Kernel (portable) | Instance (yours) |
|---|---|---|
| The ten top-level folders | ✅ identical for every company | — |
| Subfolders of `Input/`, `Output/`, `CRM/`, `Resources/` | ✅ | — |
| Domains in `Knowledge/` | the convention | ❌ the domains reflect the business |
| `#type/*` | ✅ full set | — |
| `#domain/*` | the namespace | ❌ the values |
| Tier 2 (`crm/*`, `customer/*`) | `crm/*` | the rest depends on the business |
| Governance properties | ✅ the set and the policy | ❌ owners, cadences, audiences |
| `_system/` memory schema | ✅ folders and lifecycle | ❌ contents |
| `_system/agent/` | ✅ the three files as templates | ❌ identity, people, priorities |
| Contracts (`_tags.md`, `object-schema.md`) | ✅ with values to customize | — |
| `.base` views | ✅ base set | your specific views |
| Agents and automations | ✅ the six bundles, all `report` or `propose` by default | which ones you enable, and in which mode |
| Living documents in `Knowledge/Company/` | ✅ the five files and their sections | ❌ the content |

**This template = kernel + empty instance**: complete structure, filled contracts, one sample project, one MOC, a handful of fictional notes to show the graph, and zero real content. Whoever receives it must be able to write the first note within a minute without having read this file. The `onboard` skill of the plugin interviews the team and fills the instance.

### Personal brain vs company brain

Same primitives, different governance.

| | Personal brain | Company brain |
|---|---|---|
| Ownership | yours, follows you between jobs | the organization's |
| Heart | memory, decisions, point of view | living documents, customer knowledge, decision log |
| `CRM/` | personal network | accounts and stakeholders |
| `Knowledge/` | your concepts | shared domain, terminology |
| `Journal/` | personal daily | operational log, meetings |
| Governance | you are the only author | review: who writes, who approves |
| Main risk | accumulation without synthesis | drift between documents and reality |

The company brain adds **one structural requirement**: living documents have a declared owner and a review date. The rest of the kernel is identical, which is why someone with a personal brain already knows how to build the company one.

---

## 9. Sacred rules

Invariants. The first three have no exceptions; the others carry their reason so an agent can adapt with judgment.

1. **Never files or folders at the root** (except the contract files). A new root folder is a signal of intrusion.
2. **Never delete**: archive.
3. **Synced sources: graph-additive only.**
4. **Every new note has 1 to 4 tags.** Without tags it does not compose.
5. **Living documents carry `owner` and `review_due`.** Without them nobody keeps them true.
6. **Ask before overwriting** what was not asked for.
7. **Wikilinks, never markdown links**, for internal references.
8. **Search before asking.** If a name is verifiable, verify it.
9. **The current conversation beats recalled memory.**
10. **Nothing leaves the brain without a go**: no sending, publishing, executing.

---

## 10. How the brain grows, improves and stays true

The loop, and who runs each step:

| Step | What happens | Who | Cadence |
|---|---|---|---|
| **Capture** | everything enters raw: meetings, documents, conversations, chat | people, syncs, the `capture` and `meeting` skills | continuous |
| **Compile** | inputs become minutes, decisions, facts in living documents, CRM updates | agents during work; the triage automation | same turn, daily |
| **Query** | questions answered from the brain with citations; gaps named | the `ask` skill | on demand |
| **Promote** | inputs that keep being cited become concepts; domains over 50 notes get a MOC; terms enter the glossary | the `promote` skill, the weekly review | weekly |
| **Maintain** | links, tags, indices, orphans, root guard, secrets | the librarian automation, the guard hook, CI | on write, weekly |
| **Verify** | living documents past `review_due` go back to their owner | the health check, the brief, the owner | per cadence |
| **Review** | what the brain learned this week, what is stale, up to 5 proposals | the weekly review automation | weekly |
| **Measure** | notes updated, decisions recorded, `Input:Knowledge`, stale living docs, answered-from-brain rate, reverts | the health script, the weekly review | weekly |
| **Evolve** | structure, tags, rules and automations change by decision | the brain owner | when a decision says so |

**Metrics that mean something** (the health script computes them):

- *Living documents stale*: count and oldest. Target: zero past twice the cadence.
- *Input : Knowledge ratio*: see section 5.
- *Orphans and broken links*: trend, not absolute.
- *Decisions per week*: a company that takes decisions and records none has a brain that does not know why things are the way they are.
- *Meetings with minutes*: of the meetings synced this week, how many have a minutes note. Target 80%.
- *Reverts of agent writes*: above 10% of writes for two weeks, lower the autonomy of that automation.

---

## Sources of truth

If this file and one of these diverge, the more specific one wins:

- [[_tags]]: the tag registry
- [[object-schema]]: frontmatter per type, governance cadences
- [[brain-context]]: the map of this instance
- `AGENTS.md` / `CLAUDE.md`: the behavior contract of agents
