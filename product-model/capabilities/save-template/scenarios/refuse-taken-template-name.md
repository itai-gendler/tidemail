---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person types the name of an existing template and presses Enter
  kind: actor
  actor: user
  entities:
  - entity: template
    effect: reads
    facts:
    - Name
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail says the name already exists and suggests editing that template instead
  kind: product
  actor: user
  entities:
  - entity: template
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
---

# Refuse a name already taken

## Trigger

The name is in use.

## Outcome

Nothing is saved.

## Edge cases

- Names can't start with a dot or contain / \ :, and are at most 60 characters.
- With nothing written yet, there is nothing to save.
