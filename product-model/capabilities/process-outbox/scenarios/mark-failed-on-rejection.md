---
kind: edge
routes:
  tui: TideMail
steps:
- text: The SMTP server rejects it permanently, or the last allowed attempt fails
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
- text: TideMail marks it failed with the server's reason, credentials left out
  kind: product
  entities:
  - entity: outgoing-message
    effect: changes
    from: Sending
    to: Failed
    facts:
    - Last error
  contexts:
    tui:
      place: tidemail::outbox
---

# Fail at once on a permanent rejection

## Trigger

The server refused the message, or every attempt is spent.

## Outcome

The message waits in the Outbox for the person to fix and retry or edit it; the status bar reports it.

## Edge cases

- A permanent (5xx) rejection is not retried, whatever attempts remain.
