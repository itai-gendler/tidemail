---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `x` in Contacts and chooses where to save the file
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::contacts
- text: TideMail writes contacts.vcf there with every contact and says where
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
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

# Export contacts as vCard

## Trigger

The person moves contacts to another app.

## Outcome

A vCard file holds all the contacts.
