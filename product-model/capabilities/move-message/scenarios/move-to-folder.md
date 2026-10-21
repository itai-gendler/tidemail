---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `m` on a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::message-list
- text: The person chooses the destination folder in the picker
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail takes the message out of the list, waits six seconds, then moves it on the server
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

# Move a message to a folder

## Trigger

The person files a message.

## Outcome

The message is in the chosen folder on the server.

## Edge cases

- Messages move only between folders of one account.
