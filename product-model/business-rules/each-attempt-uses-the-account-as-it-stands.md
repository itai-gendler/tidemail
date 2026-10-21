---
appliesTo:
- type: capability
  id: process-outbox
- type: capability
  id: retry-send
references:
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#ResolveOutboxAccount
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#OutboxMessage
---

# Every delivery attempt sends from the account as it stands at that moment

A queued message keeps the account's id, not a copy of its settings, so correcting an account's From address or servers and retrying is enough; the message does not need writing again. Each attempt checks the recipients and sender address again first.
