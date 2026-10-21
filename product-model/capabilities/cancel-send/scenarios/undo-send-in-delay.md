---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+Z within the send delay
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail takes it out of the Outbox, keeps it as a draft and reopens it in compose
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: removes
    from: Queued
  - entity: draft
    effect: creates
    facts:
    - Sending account
    - To
    - Cc
    - Bcc
    - Subject
    - Body
    - Attachments
    - In reply to
    - Last saved
  contexts:
    tui:
      place: tidemail::compose
---

# Undo a send during the delay

## Trigger

The person spotted a mistake just after sending.

## Outcome

Nothing was sent; the message is back in compose to fix.
