---
appliesTo:
- type: entity
  id: message
  effect: creates
permits:
- actors:
  - user
- unattended: true
references:
- kind: doc
  role: intent
  target: docs/cli.md
---

# Only the person's syncs and TideMail's own refreshes bring mail into the cache

Mail enters the cache from the server when the person syncs or pages back, or when an account refreshes on its own; the command line and agents only read what is already cached.
