---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `d` on a message
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
- text: TideMail takes it out of the list, waits six seconds, then moves it to Trash on the server
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

# Delete a message to Trash

## Trigger

The person no longer wants a message.

## Outcome

The message is in Trash.
