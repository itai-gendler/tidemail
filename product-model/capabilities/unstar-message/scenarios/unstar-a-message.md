---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `*` on a starred message
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
- text: TideMail clears the flag on the server and in the list
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

# Unstar a message

## Trigger

A starred message no longer needs the star.

## Outcome

The star is gone here and in other clients.
