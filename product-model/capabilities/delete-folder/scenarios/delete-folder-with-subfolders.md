---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `d` on a folder
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
- text: TideMail asks, saying how many subfolders go with it and that every message in them is deleted
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: The person confirms with `y` or Enter
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail deletes the folder and its subfolders on the server and drops them and their messages from the cache
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: removes
  - entity: message
    effect: removes
    with: folder
  contexts:
    tui:
      place: tidemail::sidebar
---

# Delete a folder with its subfolders

## Trigger

The person no longer needs a folder or anything in it.

## Outcome

The folder, its subfolders and their mail are gone from the server and from TideMail.

## Edge cases

- Deleting is refused when a system folder, such as a Sent subfolder, is inside it.
