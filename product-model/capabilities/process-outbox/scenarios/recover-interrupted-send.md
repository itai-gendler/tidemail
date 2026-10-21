---
kind: unattended
routes:
  tui: TideMail
steps:
- text: TideMail starts and finds an outgoing message whose delivery attempt was cut off mid-flight
  kind: condition
  unattended: true
  entities:
  - entity: outgoing-message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail marks it uncertain with a note to check Sent mail before retrying
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
- text: TideMail schedules the queued outgoing messages again for their due times
  kind: product
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Next attempt
  contexts:
    tui:
      place: tidemail::outbox
---

# Find an interrupted send at startup

## Trigger

TideMail quit or crashed during a delivery.

## Outcome

No message is sent twice by accident, and queued ones keep their times.
