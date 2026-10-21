---
domain: compose
availability:
- place: tidemail
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/ui/compose.go#send
- kind: code
  role: implementation
  target: internal/ui/send_undo.go#handleSendQueued
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#Enqueue
- kind: code
  role: implementation
  target: internal/mailapp/prepare.go#Prepare
- kind: code
  role: implementation
  target: internal/cli/mail.go#runComposeCLI
- kind: code
  role: implementation
  target: internal/cliform/compose.go
- kind: doc
  role: intent
  target: docs/cli.md
---

# Send message

Hand a finished message to the Outbox. In compose Ctrl+S checks the recipients and the sending account's address and queues the message for the send delay (5 seconds by default), during which Ctrl+Z takes it back. From the command line, `tidemail send` saves a draft unless the invocation authorizes delivery with `--yes` or an approved review; an authorized send needs recipients, a subject and a body or attachment, and is queued for the client or `tidemail outbox process` to deliver.
