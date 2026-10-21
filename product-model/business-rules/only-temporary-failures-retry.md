---
appliesTo:
- type: capability
  id: process-outbox
- type: capability
  id: retry-send
references:
- kind: code
  role: implementation
  target: internal/smtp/smtp.go#CanRetry
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#Deliver
---

# Only a temporary delivery failure is retried on its own

A connection failure or a temporary (4xx) reply puts the message back in the queue for one minute later, while attempts remain under the limit, which counts the first try and is 3 by default. A permanent (5xx) rejection fails the message at once, whatever attempts remain. A failed message waits for the person.
