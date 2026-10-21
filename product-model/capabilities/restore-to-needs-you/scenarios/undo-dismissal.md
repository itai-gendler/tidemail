---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+Z in Needs You just after dismissing a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::needs-you
- text: TideMail clears the dismissal and the message is back in Needs You
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Dismissed from Needs You
  contexts:
    tui:
      place: tidemail::needs-you
---

# Undo a dismissal straight away

## Trigger

The person dismissed the wrong message.

## Outcome

The message is listed in Needs You again.
