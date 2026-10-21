---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person moves to a folder in the left pane
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - Unread count
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail lists the folder's cached messages, newest first
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Subject
    - Date
    - Read
    - Starred
    - Attachments
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
- text: The person presses `u` to see only unread mail
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
---

# Browse a folder

## Trigger

The person wants to see what is in a folder.

## Outcome

The folder's messages are listed, narrowed to unread ones.

## Edge cases

- `t` lists starred messages first and is remembered across restarts.
- `g` groups the list into conversations by their Message-ID headers.
