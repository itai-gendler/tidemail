---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `H` on a folder
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
- text: TideMail marks it hidden and leaves it and its subfolders out of the sidebar
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

# Hide a folder from the sidebar

## Trigger

A folder clutters the sidebar but must stay on the server.

## Outcome

The folder no longer shows; the status line says Show hidden folders brings it back.
