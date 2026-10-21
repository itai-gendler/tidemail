---
appliesTo:
- type: capability
  id: delete-message
- type: capability
  id: archive-message
- type: capability
  id: move-message
- type: capability
  id: undo-message-action
references:
- kind: code
  role: implementation
  target: internal/ui/destructive_undo.go
---

# Delete, archive and move wait six seconds before reaching the server

The message leaves the list at once, but the server is told only after six seconds, so Ctrl+Z can take back the latest one. Needs You's count follows at once and is restored by an undo or a failure.
