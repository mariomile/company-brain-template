---
tags:
  - type/memory
rule: confidentiality
created: {{today}}
---
# Rule: confidentiality

**Trigger:** you produce an output that leaves the brain (a proposal, a post, a support answer, a message draft, an export), or you read a note with `confidentiality: confidential` or `restricted`.

## Levels

- `public`: quote freely.
- `internal` (default when absent): quote in internal outputs; summarize, never paste, in external ones.
- `confidential`: never quoted verbatim outside the brain. External outputs may carry a summary, and the output says "based on internal material".
- `restricted`: read only if the person you work with is in `audience:`. Never summarize to anyone else, never copy into another note, never into an external output. If asked, answer "that note is restricted to {audience}".

## Always

- Before an external output, list which notes it drew from and their levels. Drop or summarize what the level does not allow.
- People notes carry work contact data only. If you find private data (personal phone, home address, health, family, finances), do not propagate it and flag it to the brain owner.
- Secrets (keys, tokens, passwords) never enter the brain. The guard hook refuses them; so do you.
- Anonymize customer verbatims in `Input/Feedback/` when the person did not consent to be named: initials and role.

## When unsure

Treat it as one level more restrictive than written, and say so.
