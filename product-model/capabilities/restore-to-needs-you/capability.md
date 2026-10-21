---
domain: needs-you
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/needs_you.go#undoNeedsYouDismissal
- kind: code
  role: implementation
  target: internal/ui/needs_you.go#executeNeedsYouCommand
---

# Restore to Needs You

Bring a dismissed message back into Needs You: Ctrl+Z right after dismissing it, or Restore to Needs You in the command palette on the message opened from its folder.
