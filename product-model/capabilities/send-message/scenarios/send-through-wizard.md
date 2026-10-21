---
kind: alternate
routes:
  cli: Command line
steps:
- text: The person runs `tidemail send` in a terminal and fills in the account, recipients, subject, body, signature choice and attachments
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
- text: TideMail shows the review, with Save draft selected
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
- text: The person chooses Send email
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail queues the outgoing message and counts down the send delay with `u` or Ctrl+Z to undo, then delivers it and shows the result
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
  - entity: settings
    effect: reads
    facts:
    - Send delay
    - Skip review step
    - Include signature by default
  contexts:
    cli:
      place: command-line
---

# Send through the compose wizard

## Trigger

The person sends a message from a terminal without opening the client.

## Outcome

The message is delivered, or the recorded failure is shown.

## Edge cases

- Sending always needs Send email chosen explicitly, even when the wizard was opened with --yes.
- Selected files are read before review, so changing them afterwards does not change the approved message.
