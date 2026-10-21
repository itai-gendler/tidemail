---
kind: unattended
routes:
  tui: TideMail
steps:
- text: A snoozed conversation's wake time arrives while the person is still waiting on it
  kind: condition
  unattended: true
  entities:
  - entity: conversation
    effect: reads
    facts:
    - Snoozed until
  contexts:
    tui:
      place: tidemail::waiting-on-them
- text: TideMail ends the snooze and lists the conversation in Waiting on Them again
  kind: product
  entities:
  - entity: conversation
    effect: changes
    from: Snoozed
    to: Waiting
    facts:
    - Snoozed until
  contexts:
    tui:
      place: tidemail::waiting-on-them
---

# Wake a conversation at its time

## Trigger

The snooze time comes.

## Outcome

The conversation waits in Waiting on Them again.
