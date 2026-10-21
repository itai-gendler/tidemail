---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `c`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail opens compose from the default account, with its signature
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Default account
  - entity: account
    effect: reads
    facts:
    - From address
    - Signature
  contexts:
    tui:
      place: tidemail::compose
- text: The person fills in To, picking a suggested contact, then the subject and body
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
      place: tidemail::compose
- text: TideMail saves the draft under the sending account as the person types
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
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
---

# Write a new message

## Trigger

The person wants to write to someone.

## Outcome

A draft is kept and the message is ready to send.

## Edge cases

- Without a default account, compose starts from the first account.
- Ctrl+U cycles the sending account; Enter or Space on the From row opens the account picker.
