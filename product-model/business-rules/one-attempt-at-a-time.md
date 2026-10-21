---
appliesTo:
- type: entity
  id: outgoing-message
  effect: changes
  from: Queued
  to: Sending
references:
- kind: code
  role: implementation
  target: internal/db/outbox.go#ClaimDueOutbox
---

# One delivery attempt at a time can claim a message

An attempt claims the message before contacting the server, so the client and any number of `outbox process` runs never deliver the same message twice, and a message being sent cannot be edited, cancelled or retried until its attempt ends.
