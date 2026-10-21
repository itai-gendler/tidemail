---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `d` on a message in Trash
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
  - entity: folder
    effect: reads
    facts:
    - Name
    - Kind
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail waits six seconds, then deletes it from the server and the cache
  kind: product
  actor: user
  entities:
  - entity: message
    effect: removes
  contexts:
    tui:
      place: tidemail::message-list
---

# Delete a message for good from Trash

## Trigger

The person empties a message out of Trash.

## Outcome

The message is gone from the server.

## Edge cases

- An account without a Trash folder deletes for good from any folder.
