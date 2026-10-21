---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person selects contacts with Space in Contacts and presses `c`
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
- text: TideMail opens compose from the default account with the selected contacts in To
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - Name
    - Email
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
- text: The person writes the subject and body
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail saves the draft as the person types
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: creates
    facts:
    - Sending account
    - To
    - Cc
    - Bcc
    - Subject
    - Body
    - Attachments
    - In reply to
    - Last saved
  contexts:
    tui:
      place: tidemail::compose
---

# Write to contacts selected in Contacts

## Trigger

The person wants to write to several saved contacts.

## Outcome

A draft addressed to them is kept and ready to send.
