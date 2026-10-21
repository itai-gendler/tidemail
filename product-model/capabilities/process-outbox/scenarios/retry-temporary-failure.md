---
kind: edge
routes:
  tui: TideMail
steps:
- text: A delivery attempt fails with a temporary error, such as a lost connection or a 4xx reply, and attempts remain
  kind: condition
  unattended: true
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Attempts
    - Attempt limit
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail queues it again for one minute later and says which retry is next
  kind: product
  entities:
  - entity: outgoing-message
    effect: changes
    from: Sending
    to: Queued
    facts:
    - Next attempt
    - Last error
  contexts:
    tui:
      place: tidemail::outbox
---

# Retry after a temporary failure

## Trigger

The server or the network had a passing problem.

## Outcome

The message tries again a minute later; the status bar shows retrying in the Outbox.
