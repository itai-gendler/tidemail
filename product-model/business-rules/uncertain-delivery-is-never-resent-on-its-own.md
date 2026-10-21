---
appliesTo:
- type: entity
  id: outgoing-message
  to: Uncertain
- type: capability
  id: retry-send
references:
- kind: code
  role: implementation
  target: internal/db/outbox.go#RecoverOutbox
- kind: code
  role: implementation
  target: internal/smtp/smtp.go
---

# A delivery that may have happened is never resent on its own

When the connection goes while the server is accepting a message, or TideMail finds an attempt cut off at startup, the message is marked uncertain. Only the person retries it, and the client asks first because the server may already have delivered it.
