---
appliesTo:
- type: entity
  id: draft
  effect: changes
permits:
- actors:
  - user
references:
- kind: doc
  role: intent
  target: docs/cli.md
---

# Only the person edits a draft

Drafts are edited in compose. Agents can create drafts but have no way to change one; `drafts.edit` is reserved for a future command.
