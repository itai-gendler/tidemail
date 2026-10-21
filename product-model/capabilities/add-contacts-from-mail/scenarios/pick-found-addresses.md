---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `f` in Contacts
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::contacts
- text: TideMail lists the addresses in cached mail that are not contacts yet, by name
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - To
  - entity: contact
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::contacts
- text: The person marks several with Space and presses `a`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::contacts
- text: TideMail saves them as contacts with the names found in mail
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: creates
    facts:
    - Email
    - Name
  contexts:
    tui:
      place: tidemail::contacts
---

# Add found addresses as contacts

## Trigger

The person writes to people already in their mail.

## Outcome

Those people are contacts.
