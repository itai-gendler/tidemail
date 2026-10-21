---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/destructive_undo.go#scheduleDelete
- kind: code
  role: implementation
  target: internal/ui/messages.go#remoteDeletePlan
---

# Delete message

Delete messages (`d`). After six seconds TideMail moves them to the account's Trash on the server; in Trash, or on an account without one, they are deleted for good. Deleting several selected messages asks first.
