---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `x` on an unread message
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
- text: TideMail sets the read flag on the server, then in the cache, and moves to the next message
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

# Mark a message read

## Trigger

The person has dealt with a message without opening it.

## Outcome

The message is read on the server and in TideMail.

## Edge cases

- With messages selected (Space), `x` marks the whole selection.
- If the server refuses, the message keeps its old state and the reason is shown.
