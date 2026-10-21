---
kind: unattended
routes:
  tui: TideMail
steps:
- text: A queued outgoing message's send delay or scheduled time has passed while the client runs
  kind: condition
  unattended: true
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Next attempt
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail claims it for one delivery attempt
  kind: product
  entities:
  - entity: outgoing-message
    effect: changes
    from: Queued
    to: Sending
    facts:
    - Attempts
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail sends it through the sending account's SMTP server as that account now stands
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - SMTP server
    - From address
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail records it as sent, files a copy in the account's Sent folder and deletes its draft
  kind: product
  entities:
  - entity: outgoing-message
    effect: changes
    from: Sending
    to: Sent
    facts:
    - Content
  - entity: draft
    effect: removes
  - entity: account
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail syncs the account's Sent folder and says message sent
  kind: product
  entities:
  - entity: message
    effect: creates
    facts:
    - From
    - To
    - Subject
    - Date
    - Body
    - Folder
  - entity: account
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
---

# Deliver a due message

## Trigger

The undo window ends.

## Outcome

The mail is delivered and in Sent; the stored copy can start a wait in Waiting on Them.

## Edge cases

- Gmail files what it sends by SMTP itself, so no copy is added there.
- If filing the copy fails, the message still counts as sent and the status line says no copy was saved.
