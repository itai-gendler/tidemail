---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+S in compose
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - To
    - Cc
    - Bcc
    - Subject
    - Body
    - Attachments
    - Sending account
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail checks the addresses and the sending account's From address, adds the signature and queues it as an outgoing message, due after the send delay
  kind: product
  actor: user
  entities:
  - entity: account
    effect: reads
    facts:
    - From address
    - Signature
  - entity: settings
    effect: reads
    facts:
    - Send delay
    - Maximum attempts
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
- text: TideMail closes compose and says it is sending, with Ctrl+Z to undo
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Next attempt
  contexts:
    tui:
      place: tidemail::message-list
---

# Send with an undo window

## Trigger

The message is finished.

## Outcome

The message waits in the Outbox for the send delay, then leaves; its draft goes once it is delivered.

## Edge cases

- A message with no subject can be sent from compose.
- If the message cannot be queued, compose stays open with everything in it.
