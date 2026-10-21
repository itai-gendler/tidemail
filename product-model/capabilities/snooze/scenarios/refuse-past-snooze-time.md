---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person chooses Pick date/time and types a time that has already passed
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::needs-you
- text: TideMail says the time is in the past and snoozes nothing
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::needs-you
---

# Refuse a time in the past

## Trigger

The typed time is not in the future.

## Outcome

Nothing is snoozed; the person can type another time as YYYY-MM-DD HH:MM.
