---
appliesTo:
- type: capability
  id: add-account
- type: capability
  id: edit-account
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#saveAccountCmd
---

# An account is saved only after its server accepts it

Saving checks every row first, then signs in to the IMAP server and lists its folders; any failure keeps nothing.
