---
kind: edge
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+Z more than six seconds after archiving a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
- text: The archive has already been sent to the server
  kind: condition
  entities:
  - entity: message
    effect: reads
    facts:
    - Folder
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail has nothing left to undo and leaves the message archived
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
---

# Undo after the action reached the server

## Trigger

The undo window has passed.

## Outcome

The message stays in the Archive folder; the person can move it back.
