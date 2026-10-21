---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/compose.go#NewForward
- kind: code
  role: implementation
  target: internal/ui/commands.go#executeCommand
---

# Forward

Pass a message on (`f`): compose opens with the original's readable text quoted and its attachments kept.
