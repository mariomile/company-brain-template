# Automations

Scheduled runs. One file per run: its frontmatter says when it runs and what it may touch, its body is the whole prompt. The plugin's `brain run <name>` prints it, ready for any runtime.

| Field | Meaning |
|---|---|
| `when` | schedule, human-readable (`daily 07:30`, `weekly Fri 16:00`) |
| `mode` | `report` (writes only its report), `propose` (writes proposals for a person, changes nothing else), `act` (applies changes inside `scope`) |
| `scope` | globs this run may write besides its report, its proposals, `_system/log.md` and one line in today's daily note |
| `skill` | the `company-brain` skill whose procedure the run follows |
| `enabled` | `false` until a person turns it on |

`mode` is the only autonomy setting. Climbing from `propose` to `act` is a decision of the brain owner, after two weeks of proposals that were accepted as they were.

All ship **disabled**. Turn them on one at a time, in this order:

1. `morning-brief` (report)
2. `inbox-triage` (propose)
3. `meeting-minutes` (propose)
4. `weekly-review` (propose)
5. `librarian` (act, narrow scope)
6. `ingest` (propose, needs connected sources in `_system/sources.md`)

**Who runs them.** The template ships `.github/workflows/brain-routines.yml`: GitHub runs them on schedule with Claude Code, posts reports to one rolling issue and opens a pull request for proposals and changes. Any other scheduler works the same way: `brain run <name> | claude -p`, then `brain scope <name>` to check the run stayed inside its scope, then `brain sync`. Exo inside Obsidian reads this folder natively.

Each file ends with `## Lessons`: what this run learned about doing its job here, a few lines, replaced rather than appended. Facts about the company never go there.
