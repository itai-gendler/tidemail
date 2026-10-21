---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+Z within six seconds of deleting a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail cancels the pending delete and puts the message back in the list
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
    - Folder
  contexts:
    tui:
      place: tidemail::message-list
---

# Undo a delete in time

## Trigger

The person deleted the wrong message.

## Outcome

Nothing reached the server; the message stays where it was.

## Edge cases

- Ctrl+Z first cancels a send still in its undo window, then undoes a Needs You dismissal or a Stop waiting in those views, then the latest message action.
