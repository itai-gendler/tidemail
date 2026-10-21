---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `R` on a folder
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
- text: TideMail marks every cached message in it read and clears its unread count
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Read
  - entity: folder
    effect: changes
    facts:
    - Unread count
  contexts:
    tui:
      place: tidemail::sidebar
---

# Mark a folder read

## Trigger

The person wants a clean slate in a folder.

## Outcome

Nothing in the folder is unread.

## Edge cases

- On an account row, `R` marks every folder of that account.
