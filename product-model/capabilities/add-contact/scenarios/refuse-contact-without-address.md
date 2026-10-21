---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person saves the contact form with the address empty
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::contacts
- text: TideMail says the address is required and saves nothing
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::contacts
---

# Refuse a contact without an address

## Trigger

The form has no address.

## Outcome

The form stays open.
