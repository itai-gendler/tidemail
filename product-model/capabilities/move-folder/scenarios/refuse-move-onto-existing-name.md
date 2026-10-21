---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses `<` on a folder whose name already exists beside its parent
  kind: actor
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - Parent
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail refuses the move up front and changes nothing
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
---

# Refuse a move onto an existing name

## Trigger

The destination already has a folder with that name.

## Outcome

The folder stays where it was.
