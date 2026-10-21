---
kind: primary
result: achieved
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+U while reading list mail whose unsubscribe target is an email address
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
  contexts:
    tui:
      place: tidemail::message
  capability: unsubscribe-from-mailing-list
- text: TideMail opens compose addressed to the unsubscribe address with the subject it asks for
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
  capability: unsubscribe-from-mailing-list
- text: The person checks the prefilled To and subject and presses Ctrl+S
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

# Unsubscribe by sending the prefilled message

## Trigger

The person no longer wants a mailing list.

## Outcome

The unsubscribe request leaves after the send delay.
