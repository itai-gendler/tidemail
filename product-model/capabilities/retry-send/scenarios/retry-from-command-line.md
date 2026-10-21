---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail outbox retry 42 --yes --json`
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail queues the failed send again and returns state queued
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: changes
    from: Failed
    to: Queued
    facts:
    - Attempts
    - Attempt limit
    - Next attempt
    - Last error
  contexts:
    cli:
      place: command-line
---

# Retry from the command line

## Trigger

A script inspected a failure and retries it.

## Outcome

The message waits for the next queue processing.

## Edge cases

- Without --yes the retry is refused with approval_required and exit code 3.
