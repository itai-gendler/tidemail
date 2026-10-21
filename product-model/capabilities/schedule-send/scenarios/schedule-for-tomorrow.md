---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person chooses Schedule send in compose's command palette, then Tomorrow at 9:00
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - To
    - Subject
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail runs the usual send checks and queues the outgoing message due at 9:00 tomorrow
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
---

# Schedule a message for tomorrow morning

## Trigger

The message should arrive at the start of the next working day.

## Outcome

The Outbox holds it until 9:00 tomorrow; the status line shows the time.
