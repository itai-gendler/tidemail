---
domain: outbox
availability:
- place: tidemail
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/ui/outbox.go#retryOutbox
- kind: code
  role: implementation
  target: internal/db/outbox.go#RetryOutbox
- kind: code
  role: implementation
  target: internal/cli/mail.go#runOutboxAction
---

# Retry send

Try a failed outgoing message again (`r` in the Outbox, or `tidemail outbox retry ID --yes`). The tries start over with the current attempt limit. An uncertain message may already have been delivered, so the client asks before retrying it.
