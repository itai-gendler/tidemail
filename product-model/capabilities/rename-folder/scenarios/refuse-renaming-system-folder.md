---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses `r` on the Sent folder
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - Kind
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail says system folders can't be renamed or deleted
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::sidebar
---

# Refuse to rename a system folder

## Trigger

The person tries to rename Inbox, Sent, Drafts, Trash, Junk, Archive or a Gmail system label.

## Outcome

Nothing changes.
