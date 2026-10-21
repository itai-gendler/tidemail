---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person chooses Show hidden folders in the command palette
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: The person presses `H` on a folder marked (hidden)
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - Hidden
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail shows the folder again
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: changes
    facts:
    - Hidden
  contexts:
    tui:
      place: tidemail::sidebar
---

# Unhide a folder

## Trigger

The person wants a hidden folder back.

## Outcome

The folder is in the sidebar again, hidden folders or not.
