---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person picks Custom date and time and enters a time earlier today
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail asks for a future time and queues nothing
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
---

# Refuse a time that has passed

## Trigger

The chosen moment is in the past.

## Outcome

The message stays in compose.
