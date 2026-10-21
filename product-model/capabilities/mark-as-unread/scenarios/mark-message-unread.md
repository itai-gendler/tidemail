---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `x` on a read message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Read
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail clears the read flag on the server, then in the cache
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Read
  contexts:
    tui:
      place: tidemail::message-list
---

# Mark a message unread

## Trigger

The person wants to come back to a message.

## Outcome

The message is unread again everywhere.
