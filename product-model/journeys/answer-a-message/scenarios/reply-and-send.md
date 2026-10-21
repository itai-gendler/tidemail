---
kind: primary
result: achieved
routes:
  tui: TideMail
steps:
- text: The person presses `r` while reading a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Subject
  contexts:
    tui:
      place: tidemail::message
  capability: reply-to-message
- text: TideMail opens compose addressed to the sender, with the original quoted
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Reply-To
    - Subject
    - Body
  contexts:
    tui:
      place: tidemail::compose
  capability: reply-to-message
- text: The person writes the answer above the quote
  kind: actor
  actor: user
  entities: []
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

# Reply to a message and send it

## Trigger

A message needs an answer.

## Outcome

The answer leaves after the send delay.
