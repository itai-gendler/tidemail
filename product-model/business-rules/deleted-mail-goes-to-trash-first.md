---
appliesTo:
- type: capability
  id: delete-message
- type: capability
  id: run-filter-rules
references:
- kind: code
  role: implementation
  target: internal/ui/messages.go#remoteDeletePlan
---

# Deleted mail goes to Trash first

A deleted message moves to the account's Trash. Deleting it from Trash, or from an account with no Trash folder, deletes it for good.
