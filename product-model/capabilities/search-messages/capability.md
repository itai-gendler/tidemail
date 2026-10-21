---
availability:
- place: tidemail
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/ui/sync.go#searchAllMessagesCmd
- kind: code
  role: implementation
  target: internal/db/messages.go#SearchAllMessages
- kind: code
  role: implementation
  target: internal/cli/mail_reads.go#RunMailRead
- kind: doc
  role: intent
  target: docs/guide.md
---

# Search messages

Search the cached mail of every account and folder. In the client `/` matches subject, sender, recipients and body as the person types, `#` and a tag name matches the tags on message rows, and the search stays active while the person moves through the results. `tidemail messages search` runs the same search from the command line.
