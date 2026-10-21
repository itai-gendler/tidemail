---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `s` on a folder
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail fetches the folder's messages since its last sync and stores the new ones
  kind: product
  actor: user
  entities:
  - entity: message
    effect: creates
    facts:
    - From
    - To
    - Cc
    - Reply-To
    - Subject
    - Date
    - Body
    - Attachments
    - Authentication results
    - Read
    - Starred
    - Folder
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail drops cached messages the server no longer has and takes the server's read state and stars for the rest
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Read
    - Starred
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail updates the folder's unread count and last-synced time
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: changes
    facts:
    - Unread count
    - Last synced
  contexts:
    tui:
      place: tidemail::message-list
---

# Sync the selected folder

## Trigger

The person wants this folder current now.

## Outcome

The folder's list matches the server, with new mail added and changes made in other clients applied.

## Edge cases

- A folder never synced before fetches its 100 newest messages if it is an inbox, or 25 for other folders.
- When the server has renumbered the folder, its cache is rebuilt from scratch.
- Saved filter rules run on the new messages as they arrive; mail a rule moved, archived, deleted, sent to spam or marked read is not counted or announced as new.
