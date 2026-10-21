---
domain: outbox
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/outbox.go#handleOutboxKey
- kind: code
  role: implementation
  target: internal/db/outbox.go#DeleteOutbox
---

# Clear sent message

Remove a delivered message's entry from the Outbox (`d` on a sent message). The copy in the account's Sent folder is not touched.
