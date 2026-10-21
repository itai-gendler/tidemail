---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+Z in Waiting on Them just after stopping a wait
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::waiting-on-them
- text: TideMail lists the conversation as waiting again
  kind: product
  actor: user
  entities:
  - entity: conversation
    effect: changes
    from: Stopped
    to: Waiting
    facts: []
  contexts:
    tui:
      place: tidemail::waiting-on-them
---

# Undo Stop waiting

## Trigger

The person stopped the wrong conversation.

## Outcome

The conversation is waiting again.
