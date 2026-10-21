---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `n` in Contacts and fills in the address, name, phone, organization, title and note
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::contacts
- text: The person presses Enter to save
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::contacts
- text: TideMail saves the contact and suggests it first when addressing mail
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: creates
    facts:
    - Email
    - Name
    - Phone
    - Organization
    - Title
    - Note
  contexts:
    tui:
      place: tidemail::contacts
---

# Add a contact

## Trigger

The person wants someone easy to address.

## Outcome

The contact is listed and offered first in To, Cc and Bcc.
