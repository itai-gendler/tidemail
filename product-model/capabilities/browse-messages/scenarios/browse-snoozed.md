---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person moves to Snoozed
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail lists snoozed messages and conversations, soonest to wake first, with the wake time in place of the date
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Subject
    - Snoozed until
  - entity: conversation
    effect: reads
    facts:
    - Waiting for
    - Snoozed until
  contexts:
    tui:
      place: tidemail::snoozed
---

# See what is snoozed

## Trigger

The person wants to see what will come back and when.

## Outcome

Everything snoozed is listed by wake time.
