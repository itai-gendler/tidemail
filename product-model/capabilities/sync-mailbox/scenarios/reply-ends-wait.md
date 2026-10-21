---
kind: unattended
routes:
  tui: TideMail
steps:
- text: A sync stores someone else's reply in a conversation the person is waiting on
  kind: condition
  unattended: true
  entities:
  - entity: message
    effect: reads
    facts:
    - From
  - entity: conversation
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::waiting-on-them
- text: TideMail takes the conversation out of Waiting on Them and ends any snooze on it
  kind: product
  entities:
  - entity: conversation
    effect: changes
    from: Waiting
    to: Answered
    facts:
    - Latest message
  contexts:
    tui:
      place: tidemail::waiting-on-them
---

# End a wait when someone replies

## Trigger

The other side answered.

## Outcome

Nobody is waited for; the conversation returns when the person writes again.
