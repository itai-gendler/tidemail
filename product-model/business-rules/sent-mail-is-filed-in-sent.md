---
appliesTo:
- type: capability
  id: process-outbox
- type: capability
  id: send-message
references:
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#AppendToSentFolder
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#ServerFilesSentMail
---

# Delivered mail is filed in the account's Sent folder, except on Gmail

After delivery TideMail adds a copy to the sending account's Sent folder, found by its \Sent flag or a common name. Gmail files SMTP submissions itself, so nothing is added there. A failed copy never turns a delivered message back into a failure.
