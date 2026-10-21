---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `i` in Contacts and chooses a .vcf file
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::contacts
- text: TideMail adds every card's contact, updating those whose address is already a contact, and says how many it imported
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

# Import a vCard file

## Trigger

The person moves contacts over from another app.

## Outcome

The cards are contacts in TideMail.
