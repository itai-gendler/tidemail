---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `>` on a folder
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
- text: TideMail moves it on the server into the folder just above, as its last subfolder, with its own subfolders
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: changes
    facts:
    - Name
    - Parent
  contexts:
    tui:
      place: tidemail::sidebar
---

# Nest a folder under the one above

## Trigger

The person wants to file a folder under another, even one with no subfolders yet.

## Outcome

The folder is inside its new parent on the server and in the tree.

## Edge cases

- On a server without a folder hierarchy, nesting is unavailable and says so.
