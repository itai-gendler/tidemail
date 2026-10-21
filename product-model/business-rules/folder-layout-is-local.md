---
appliesTo:
- type: entity
  id: folder
  effect: changes
  facts:
  - Hidden
  - Order
references:
- kind: code
  role: implementation
  target: internal/db/mailbox_prefs.go#SetMailboxHidden
---

# Hiding and reordering folders stays in TideMail

A hidden folder and the order of folders are remembered on this computer only; the server's folders are unchanged. Creating, renaming, deleting and moving a folder in or out of a parent are real changes on the server.
