---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Alt+F in compose and walks to a file
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: The person presses Enter on the file
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail attaches it, shows its name and size, and saves the draft
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: changes
    facts:
    - Attachments
    - Last saved
  contexts:
    tui:
      place: tidemail::compose
---

# Attach a file from the browser

## Trigger

The person needs to send a file.

## Outcome

The file is attached to the draft.
