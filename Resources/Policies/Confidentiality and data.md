---
tags:
  - type/policy
  - domain/operations
owner: "[[{{owner-brain}}]]"
review_due: {{review-date}}
last_verified: {{today}}
confidentiality: internal
---
# Confidentiality and data

1. The repository is the access boundary. Everyone with the repository sees everything in it. Content that a group must not see lives in a separate brain.
2. Every note is `internal` unless marked otherwise. `confidential` is never quoted verbatim outside the company. `restricted` names its `audience:` and is read only by them.
3. People notes hold work contact data only. No private phone numbers, home addresses, health, family or financial information. Customer verbatims are anonymized unless the person consented.
4. No secrets in the brain: keys, tokens, passwords, connection strings. The guard hook refuses them; a secret that slipped in is rotated, not just removed.
5. Before an external output, the author lists the notes it drew from and their levels (`rule-confidentiality.md`).
6. The brain owner (the `owner` above) answers questions about this policy; the rule agents apply is `rule-confidentiality.md`, see [[Brain Blueprint]] section 4. Day-to-day working agreements are in [[How We Work]].
7. Right to be forgotten: a person's note is archived with the content replaced by "removed on request, YYYY-MM-DD"; the git history is handled by the brain owner.
