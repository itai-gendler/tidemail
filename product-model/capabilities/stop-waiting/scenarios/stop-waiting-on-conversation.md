---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `X` on a conversation in Waiting on Them
  kind: actor
  actor: user
  entities:
  - entity: conversation
    effect: reads
    facts:
    - Waiting for
  contexts:
    tui:
      place: tidemail::waiting-on-them
- text: TideMail takes it out of Waiting on Them for this wait
  kind: product
  actor: user
  entities:
  - entity: conversation
    effect: changes
    from: Waiting
    to: Stopped
    facts: []
  contexts:
    tui:
      place: tidemail::waiting-on-them
---

# Stop waiting on a conversation

## Trigger

The person no longer expects or needs an answer.

## Outcome

The conversation is out of the view; if they reply and the person answers again, or the person sends a nudge, it waits again.
