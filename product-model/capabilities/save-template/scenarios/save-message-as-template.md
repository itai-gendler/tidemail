---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses F6, then `n`, types a name and presses Enter
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - Body
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail saves what the person wrote, and the subject, as a new template file under that name
  kind: product
  actor: user
  entities:
  - entity: template
    effect: creates
    facts:
    - Name
    - Subject
    - Body
  contexts:
    tui:
      place: tidemail::compose
---

# Save the message as a template

## Trigger

The person wrote something worth reusing.

## Outcome

The template is in the picker and in `tidemail templates list`.
