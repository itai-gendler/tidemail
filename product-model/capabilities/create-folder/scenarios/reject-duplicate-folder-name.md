---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person types the name of an existing sibling folder in the new-folder prompt and presses Enter
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
- text: TideMail says a folder with that name already exists and creates nothing
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::sidebar
---

# Refuse a name that already exists

## Trigger

The name is taken among its siblings.

## Outcome

No folder is created; the prompt can take another name.

## Edge cases

- Empty names, names holding the server's separator, and names with control characters, * or % are refused the same way.
