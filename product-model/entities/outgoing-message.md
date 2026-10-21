---
domain: outbox
references:
- kind: code
  role: implementation
  target: internal/db/outbox.go
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#Deliver
- kind: doc
  role: intent
  target: docs/cli.md
---

# Outgoing message

A message the person has sent, kept in the Outbox from the moment it is queued until it is delivered and after. It survives restarts, and the client or `tidemail outbox process` delivers it once it is due.

## Information kept

- **Sending account** — the account it is sent from, resolved again on every attempt
- **Recipients** — the To and Cc recipients
- **Subject** — the subject line
- **Content** — the finished message with its attachments, kept until it is delivered
- **Attempts** — how many delivery attempts have been made
- **Attempt limit** — the maximum attempts, including the first, taken from the Editor setting
- **Next attempt** — when it is due: after the send delay, at the scheduled time, or a minute after a temporary failure
- **Last error** — why the last attempt failed

## States

### Queued

Waiting until it is due: inside the undo window, scheduled for later, or waiting to retry.

### Sending

A delivery attempt has claimed it; nothing else can send or change it until the attempt ends.

### Sent

The server accepted it.

### Failed

Delivery failed and the attempts are spent, or the failure was permanent; it waits for the person.

### Uncertain

The connection went while the server was accepting it, so it may have been delivered; it is never retried on its own.
