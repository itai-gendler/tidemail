---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses `d` on a failed send
  kind: actor
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail says to use `e` to cancel delivery and move it to Drafts
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::outbox
---

# Refuse to clear an unsent message

## Trigger

The message has not been sent.

## Outcome

Nothing is removed.
