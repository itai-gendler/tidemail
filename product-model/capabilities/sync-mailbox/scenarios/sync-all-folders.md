---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `F`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: There are more than 10 folders
  kind: condition
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail asks first, since syncing them all can take a while
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: The person confirms with `y`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail syncs every folder of every account
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
    effect: changes
    facts:
    - Unread count
    - Last synced
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::sidebar
---

# Sync every folder after confirming

## Trigger

The person wants everything current.

## Outcome

Every folder is synced; with 10 folders or fewer, `F` starts without asking.
