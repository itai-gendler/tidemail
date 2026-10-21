---
domain: outbox
availability:
- place: tidemail
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/ui/send_undo.go#undoLatestPendingSend
- kind: code
  role: implementation
  target: internal/ui/outbox.go#handleOutboxKey
- kind: code
  role: implementation
  target: internal/db/outbox.go#EditOutbox
- kind: code
  role: implementation
  target: internal/cli/mail.go#runOutboxAction
---

# Cancel send

Take an unsent message back out of the Outbox into Drafts: Ctrl+Z while it waits its send delay, `e` or Enter on it in the Outbox, `u` in the command-line wizard's countdown, or `tidemail outbox cancel ID`. The move is all-or-nothing, so the message is never lost or still sendable. A message being sent or already sent cannot be cancelled.
