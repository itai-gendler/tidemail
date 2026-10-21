---
kind: alternate
routes:
  cli: Command line
steps:
- text: The person runs `tidemail send … --send-now --yes --json`
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail queues the outgoing message as due now and attempts delivery before the command exits
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
    cli:
      place: command-line
- text: TideMail returns the recorded state, sent when the server accepted it
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: changes
    from: Queued
    to: Sent
    facts:
    - Attempts
  contexts:
    cli:
      place: command-line
---

# Deliver at once from a script

## Trigger

A script needs the mail out before it finishes.

## Outcome

The message is delivered and filed in Sent; a failed or uncertain attempt exits 1.

## Edge cases

- --send-now skips the delay but does not authorize delivery by itself.
