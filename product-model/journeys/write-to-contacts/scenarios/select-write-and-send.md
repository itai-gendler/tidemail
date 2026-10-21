---
kind: primary
result: achieved
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
  capability: compose-message
- text: TideMail opens compose with them in To
  kind: product
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
  capability: compose-message
- text: The person writes the subject and body
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
  capability: compose-message
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
  capability: compose-message
- text: The person presses Ctrl+S
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - To
    - Subject
    - Body
  contexts:
    tui:
      place: tidemail::compose
  capability: send-message
- text: TideMail queues it as an outgoing message for the send delay
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: creates
    to: Queued
    facts:
    - Sending account
    - Recipients
    - Subject
    - Content
    - Attempts
    - Attempt limit
    - Next attempt
  contexts:
    tui:
      place: tidemail::compose
  capability: send-message
---

# Select contacts, write and send

## Trigger

The person wants to write to a group of people they keep as contacts.

## Outcome

The message leaves after the send delay.
