---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses `e` on a send that is under way
  kind: actor
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail says to wait for this delivery attempt to finish
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::outbox
---

# Refuse while a delivery attempt runs

## Trigger

Delivery has already started.

## Outcome

The message is left to its attempt.

## Edge cases

- A sent message offers no edit; `d` clears it instead.
