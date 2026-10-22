# Automations

Scheduled runs. Each file declares `when`, `mode` (`report` writes nothing in the brain, `propose` writes proposals, `act` writes within `scope`), `scope` (globs), an optional `agent` bundle, and `enabled`.

All ship **disabled**. Enable one at a time, in this order, and move each up the ladder only after its output has been right for two weeks:

1. `morning-brief` (report)
2. `inbox-triage` (propose, then act)
3. `meeting-minutes` (propose, then act)
4. `weekly-review` (propose)
5. `librarian` (act, narrow scope)
6. `consolidation` (act)

Who runs them: Exo (inside Obsidian) reads this folder natively. Any other scheduler (Claude Code routines, cron plus `claude -p`, a CI job) can run the same prompt with the same `mode` and `scope`; the plugin's `brain run <automation>` prints the full prompt to pipe into the runtime of your choice.
