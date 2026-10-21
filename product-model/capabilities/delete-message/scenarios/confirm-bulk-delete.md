---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person selects several messages with Space and presses `d`
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
- text: TideMail asks before deleting them
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message-list
- text: The person confirms with `y`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail waits six seconds, then moves them all to Trash
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

# Confirm deleting a selection

## Trigger

The person clears out several messages at once.

## Outcome

The selected messages are in Trash; one message alone is deleted without asking.
