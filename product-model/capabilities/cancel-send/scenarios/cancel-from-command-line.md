---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail outbox cancel 42 --json`
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail moves the queued send back to Drafts and returns state drafted
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: removes
    from: Queued
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
    cli:
      place: command-line
---

# Cancel a queued message from the command line

## Trigger

A script queued something by mistake.

## Outcome

The message is a draft in the client.
