---
kind: primary
routes:
  cli: Command line
steps:
- text: The person, or a cron entry running as them, runs `tidemail outbox process --json`
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail marks attempts abandoned for more than two minutes as uncertain
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    as: abandoned
    effect: changes
    from: Sending
    to: Uncertain
    facts:
    - Last error
  contexts:
    cli:
      place: command-line
- text: TideMail claims and delivers each outgoing message that is due, files its Sent copy and deletes its draft
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    as: due
    effect: changes
    from: Queued
    to: Sent
    facts:
    - Attempts
    - Content
  - entity: draft
    effect: removes
  contexts:
    cli:
      place: command-line
- text: TideMail returns how many it processed and exits, without waiting for sends due later
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    as: due
    effect: reads
    facts:
    - Next attempt
  contexts:
    cli:
      place: command-line
---

# Process the queue from the command line

## Trigger

The client is closed and queued mail must still leave.

## Outcome

Due mail is delivered; anything failed exits 1 and is listed in the Outbox.

## Edge cases

- A message whose account is gone is marked failed once and not reported again.
- The send delay is a minimum: a periodic processor can deliver later than the due time.
