---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+R in compose
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - Attachments
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail removes the last attached file, names it on the status line and saves the draft
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

# Remove the last attachment

## Trigger

The wrong file was attached.

## Outcome

The draft no longer carries it.
