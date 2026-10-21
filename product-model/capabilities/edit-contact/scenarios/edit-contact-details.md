---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `e` on a contact, changes the name and title, and saves
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
- text: TideMail keeps the new details
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: changes
    facts:
    - Name
    - Title
  contexts:
    tui:
      place: tidemail::contacts
---

# Change a contact's details

## Trigger

A contact's details changed.

## Outcome

The contact shows, and is suggested, with the new details.
