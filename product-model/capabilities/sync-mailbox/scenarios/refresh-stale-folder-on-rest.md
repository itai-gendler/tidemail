---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person stops on a non-inbox folder in the left pane
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
- text: The folder was last synced more than 15 minutes ago and its account is not manual only
  kind: condition
  entities:
  - entity: folder
    effect: reads
    facts:
    - Last synced
  - entity: account
    effect: reads
    facts:
    - Refresh
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail refreshes the folder quietly in the background
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
  contexts:
    tui:
      place: tidemail::message-list
---

# Refresh a stale folder when the person rests on it

## Trigger

The person opens a folder that has not been fetched for a while.

## Outcome

The folder catches up without a spinner or a keypress.

## Edge cases

- Scrolling past folders does not queue refreshes.
- Manual-only accounts refresh only when the person presses Enter, `s` or `F`.
