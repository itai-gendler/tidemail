---
kind: primary
result: achieved
routes:
  tui: TideMail
steps:
- text: The person presses `f` on a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
    - Attachments
  contexts:
    tui:
      place: tidemail::message
  capability: forward-message
- text: TideMail opens compose with the original quoted and its attachments attached
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Date
    - Subject
    - Body
    - Attachments
  contexts:
    tui:
      place: tidemail::compose
  capability: forward-message
- text: The person addresses it and adds a line
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - Name
    - Email
  contexts:
    tui:
      place: tidemail::compose
  capability: compose-message
- text: TideMail saves the draft as the person types
  kind: product
  actor: user
  entities:
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

# Forward a message and send it

## Trigger

Someone else should see a message.

## Outcome

The forward leaves after the send delay.
