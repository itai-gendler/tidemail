---
kind: edge
routes:
  tui: TideMail
steps:
- text: The connection fails while TideMail waits for the server to accept it
  kind: condition
  unattended: true
  entities: []
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail marks it uncertain and never retries it on its own
  kind: product
  entities:
  - entity: outgoing-message
    effect: changes
    from: Sending
    to: Uncertain
    facts:
    - Last error
  contexts:
    tui:
      place: tidemail::outbox
---

# Mark a send uncertain when the connection drops at acceptance

## Trigger

Delivery may have happened before the connection went.

## Outcome

The status bar reports an unconfirmed send; the person checks Sent mail before retrying by hand.
