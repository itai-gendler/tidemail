---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/messages.go#setMessageStarredCmd
---

# Unstar message

Remove the star from messages (`*` on a starred message), clearing the server's \Flagged flag.
