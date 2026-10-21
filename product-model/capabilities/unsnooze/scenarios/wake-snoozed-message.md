---
kind: unattended
routes:
  tui: TideMail
steps:
- text: A snoozed message's wake time arrives, or has passed when TideMail starts
  kind: condition
  unattended: true
  entities:
  - entity: message
    effect: reads
    facts:
    - Snoozed until
  contexts:
    tui:
      place: tidemail::needs-you
- text: TideMail ends the snooze and checks the message again with the tags it has by then
  kind: product
  entities:
  - entity: message
    effect: changes
    facts:
    - Snoozed until
  contexts:
    tui:
      place: tidemail::needs-you
- text: It is still tagged as needing the person and not dismissed
  kind: condition
  entities:
  - entity: message
    effect: reads
    facts:
    - Tags
    - Dismissed from Needs You
  contexts:
    tui:
      place: tidemail::needs-you
- text: TideMail lists it in Needs You again
  kind: product
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::needs-you
---

# Wake a message at its time

## Trigger

The snooze time comes.

## Outcome

The message reappears in Needs You without a notification; one that no longer qualifies simply stays out.
