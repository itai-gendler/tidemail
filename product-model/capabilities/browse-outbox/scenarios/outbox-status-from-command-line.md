---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail outbox status 42 --json`
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail returns that outgoing message's state, attempts, next attempt and last error
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Sending account
    - Recipients
    - Subject
    - Attempts
    - Attempt limit
    - Next attempt
    - Last error
  contexts:
    cli:
      place: command-line
---

# Check one outgoing message from the command line

## Trigger

A script checks whether its message went out.

## Outcome

The script knows whether the message is queued, sending, sent, failed or uncertain.
