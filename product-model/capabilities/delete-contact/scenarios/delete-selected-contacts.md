---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person selects contacts with Space and presses `d`
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - Name
    - Email
  contexts:
    tui:
      place: tidemail::contacts
- text: The person confirms with `y`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::contacts
- text: TideMail deletes them and says how many
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: removes
  contexts:
    tui:
      place: tidemail::contacts
---

# Delete selected contacts

## Trigger

Some contacts are no longer needed.

## Outcome

They are gone; their addresses may still be suggested from synced mail.
