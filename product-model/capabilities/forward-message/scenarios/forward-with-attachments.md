---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `f` on a message with attachments
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
- text: 'TideMail opens compose from the message''s account with Fwd: on the subject, the original quoted and its attachments attached'
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
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
---

# Forward a message with its attachments

## Trigger

The person wants someone else to see a message.

## Outcome

The forward is ready in compose with the original's files.
