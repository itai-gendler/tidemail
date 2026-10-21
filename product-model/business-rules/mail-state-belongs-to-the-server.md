---
appliesTo:
- type: capability
  id: mark-as-read
- type: capability
  id: mark-as-unread
- type: capability
  id: star-message
- type: capability
  id: unstar-message
- type: capability
  id: sync-mailbox
references:
- kind: code
  role: implementation
  target: internal/ui/messages.go#setMessageReadCmd
- kind: code
  role: implementation
  target: internal/db/reconcile.go#ApplyServerReadStates
---

# Read state, stars and folders change on the server first

Marking read or unread, starring and unstarring go to the IMAP server before the cache, and a refusal leaves the message as it was. Changes made in Gmail or another client come back on the next sync.
