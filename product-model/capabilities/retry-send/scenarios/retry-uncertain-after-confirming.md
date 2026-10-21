---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `r` on an uncertain send
  kind: actor
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail warns that delivery may have succeeded and asks to retry anyway
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::outbox
- text: The person checks Sent mail, then confirms with `y`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail queues it again
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: changes
    from: Uncertain
    to: Queued
    facts:
    - Attempts
    - Next attempt
    - Last error
  contexts:
    tui:
      place: tidemail::outbox
---

# Retry an uncertain message after confirming

## Trigger

An interrupted delivery never reached the person's Sent mail.

## Outcome

The message is sent again; any other key cancels the retry.
