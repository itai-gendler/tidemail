---
domain: outbox
availability:
- place: tidemail
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/ui/outbox.go#openOutbox
- kind: code
  role: implementation
  target: internal/ui/outbox.go#summarizeOutbox
- kind: code
  role: implementation
  target: internal/cli/mail_reads.go#RunMailRead
- kind: doc
  role: intent
  target: docs/guide.md
---

# Browse outbox

See every outgoing message across accounts: queued, sending, failed, uncertain and sent, with its tries, next attempt and last error. In the client `O` opens the Outbox and its sidebar row lists what is waiting and why; `tidemail outbox list` and `tidemail outbox status` give the same from the command line, without bodies, Bcc recipients or credentials.
