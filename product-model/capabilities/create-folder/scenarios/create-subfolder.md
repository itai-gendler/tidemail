---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `n` on a folder in the left pane
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
- text: The person types a name in the prompt row and presses Enter
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail creates the folder on the server under the selected one and shows it in the tree
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: creates
    facts:
    - Name
    - Parent
    - Kind
  contexts:
    tui:
      place: tidemail::sidebar
---

# Create a subfolder

## Trigger

The person wants a new place to file mail.

## Outcome

The new folder exists on the server and sits under its parent in the sidebar.

## Edge cases

- On a server without a folder hierarchy, names stay literal and the folder is created at the account's top level.
- While another folder change is still running on the server, `n` is refused with a short notice.
