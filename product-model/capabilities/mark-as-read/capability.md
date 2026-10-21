---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/messages.go#setMessageReadCmd
---

# Mark as read

Mark messages read (`x` on an unread message, or on a selection). The change goes to the server first, so other clients see it.
