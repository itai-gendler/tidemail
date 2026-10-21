---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `*` on an unstarred message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Starred
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail flags it on the server and stars it in the list
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Starred
  contexts:
    tui:
      place: tidemail::message-list
---

# Star a message

## Trigger

The person wants to mark a message as important to them.

## Outcome

The message is starred here and in other clients.

## Edge cases

- With several messages, `*` stars them all if any is unstarred.
