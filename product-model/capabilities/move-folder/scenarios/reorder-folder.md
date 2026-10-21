---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Shift+K on a folder whose sibling above has no open subfolders
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - Order
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail moves it above that sibling and remembers the order on this computer
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: changes
    facts:
    - Order
  contexts:
    tui:
      place: tidemail::sidebar
---

# Reorder a folder among its siblings

## Trigger

The person wants a folder higher in the tree.

## Outcome

The folder sits one place higher; nothing changes on the server.

## Edge cases

- The Inbox and system folders can be reordered but never moved in or out of a parent.
