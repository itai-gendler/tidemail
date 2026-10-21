---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+D on a message with attachments
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Attachments
  contexts:
    tui:
      place: tidemail::message
- text: The person walks to a directory in the picker and saves there
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message
- text: TideMail writes each attachment into that folder and reports where
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Attachments
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message
---

# Save attachments to a folder

## Trigger

The person wants an attachment as a file.

## Outcome

The attachments are saved on disk.
