---
kind: unattended
routes:
  tui: TideMail
steps:
- text: A sync stores the person's new message in a conversation someone else had answered
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
- text: TideMail lists the conversation in Waiting on Them again, as a new wait
  kind: product
  entities:
  - entity: conversation
    effect: changes
    from: Answered
    to: Waiting
    facts:
    - Latest message
    - Waiting since
    - Waiting for
  contexts:
    tui:
      place: tidemail::waiting-on-them
---

# Start a new wait when the person writes again

## Trigger

The person answered back or sent a nudge.

## Outcome

The conversation waits again; a Stop waiting from the earlier wait does not apply to the new one.
