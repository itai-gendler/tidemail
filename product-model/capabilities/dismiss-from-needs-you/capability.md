---
domain: needs-you
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/needs_you.go#dismissCurrent
- kind: code
  role: implementation
  target: internal/ui/needs_you.go#setDismissedCmd
- kind: doc
  role: intent
  target: docs/guide.md
---

# Dismiss from Needs You

Keep a message out of Needs You (`X` in Needs You, or Dismiss from Needs You in the command palette). The message and its tags are untouched; TideMail just remembers not to show it there, even if a plugin tags it again.
