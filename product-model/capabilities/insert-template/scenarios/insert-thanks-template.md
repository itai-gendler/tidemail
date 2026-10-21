---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses F6 in compose and moves to the Thanks template
  kind: actor
  actor: user
  entities:
  - entity: template
    effect: reads
    facts:
    - Name
    - Body
  contexts:
    tui:
      place: tidemail::compose
- text: The person presses Enter
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail inserts the template's body at the cursor as one undo step, with the first recipient's first name filled in, and saves the draft
  kind: product
  actor: user
  entities:
  - entity: template
    effect: reads
    facts:
    - Body
    - Subject
  - entity: draft
    effect: changes
    facts:
    - Body
    - Last saved
  contexts:
    tui:
      place: tidemail::compose
---

# Insert a template

## Trigger

The person sends the same kind of answer often.

## Outcome

The canned text is in the message, addressed to the recipient by name.

## Edge cases

- {first_name} becomes "there" when the first recipient has no display name; unknown tags stay as written.
