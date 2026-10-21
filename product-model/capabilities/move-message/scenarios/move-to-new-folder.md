---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `m`, then `n` in the picker, and types a new folder name
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail creates the folder on the server
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: creates
    facts:
    - Name
    - Parent
    - Kind
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail moves the message into it after the undo window
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Folder
  contexts:
    tui:
      place: tidemail::message-list
---

# Move a message into a new folder

## Trigger

The right folder does not exist yet.

## Outcome

The new folder exists and holds the message.
