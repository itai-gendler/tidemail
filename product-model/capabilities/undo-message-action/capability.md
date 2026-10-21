---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/destructive_undo.go#undoLatestDestructive
---

# Undo message action

Take back the latest delete, archive or move while it is still waiting its six seconds (Ctrl+Z).
