---
kind: primary
result: achieved
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+Z during the send delay
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message-list
  capability: cancel-send
- text: TideMail takes it out of the Outbox and reopens it in compose as a draft
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
  capability: cancel-send
- text: The person corrects the recipient
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
  capability: compose-message
- text: TideMail saves the draft
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: changes
    facts:
    - To
    - Last saved
  contexts:
    tui:
      place: tidemail::compose
  capability: compose-message
- text: The person presses Ctrl+S
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - To
    - Subject
    - Body
  contexts:
    tui:
      place: tidemail::compose
  capability: send-message
- text: TideMail queues it as an outgoing message for the send delay
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: creates
    to: Queued
    facts:
    - Sending account
    - Recipients
    - Subject
    - Content
    - Attempts
    - Attempt limit
    - Next attempt
  contexts:
    tui:
      place: tidemail::compose
  capability: send-message
---

# Undo a send, fix it and send again

## Trigger

The person notices a wrong recipient right after pressing send.

## Outcome

The corrected message leaves after the send delay; the first version never did.
