---
domain: outbox
availability:
- place: tidemail
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#Deliver
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#AppendToSentFolder
- kind: code
  role: implementation
  target: internal/smtp/smtp.go#CanRetry
- kind: code
  role: implementation
  target: internal/db/outbox.go#RecoverStaleOutbox
- kind: code
  role: implementation
  target: internal/ui/outbox.go#handleOutboxSent
- kind: code
  role: implementation
  target: internal/cli/mail.go#runOutboxAction
- kind: doc
  role: intent
  target: docs/cli.md
---

# Process outbox

Deliver the outgoing messages that are due. The client does it on its own while it runs; without the client, `tidemail outbox process` delivers what is due and exits, for example from cron. Each attempt is claimed first, so several processors never send one message twice. A delivered message is filed in the account's Sent folder (Gmail files its own) and its draft is deleted.
