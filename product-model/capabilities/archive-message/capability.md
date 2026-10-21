---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/destructive_undo.go#scheduleArchive
- kind: code
  role: implementation
  target: internal/db/accounts.go#FindArchiveMailbox
---

# Archive message

Move messages to the account's Archive folder (`a`). TideMail waits six seconds before telling the server, so Ctrl+Z can take it back.
