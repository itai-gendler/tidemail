---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `r` on a folder and types the new name
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
- text: TideMail renames it on the server, with every subfolder, and keeps its place in the tree
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: changes
    facts:
    - Name
  contexts:
    tui:
      place: tidemail::sidebar
---

# Rename a folder and its subtree

## Trigger

The folder's name no longer fits what it holds.

## Outcome

The folder and its subfolders carry the new name on the server and in TideMail.

## Edge cases

- A rename is refused up front when any subfolder would land on an existing folder.
