---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/move_picker.go
- kind: code
  role: implementation
  target: internal/ui/destructive_undo.go#scheduleMove
---

# Move message

Move messages to another folder of the same account (`m`). The picker lists the account's folders and can create a new one with `n`; the move waits six seconds so Ctrl+Z can undo it.
