---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `a` on a message
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
- text: TideMail takes the message out of the list and waits six seconds
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail moves it to the account's Archive folder on the server
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Folder
  - entity: account
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
---

# Archive a message

## Trigger

The person is done with a message but wants to keep it.

## Outcome

The message is in the Archive folder on the server.

## Edge cases

- With messages selected, `a` archives the whole selection as one action.
- The Archive folder is the one flagged \Archive by the server, or one with a common archive name.
