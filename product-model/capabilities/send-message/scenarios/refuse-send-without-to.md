---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+S in compose with the To row empty
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - To
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail says TO is required and keeps compose open
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
---

# Refuse a message with no To

## Trigger

The message has no recipient in To.

## Outcome

Nothing is queued.

## Edge cases

- An address that does not parse in To, Cc or Bcc is refused the same way.
- A sending account whose From address is not a valid address is refused before queueing.
