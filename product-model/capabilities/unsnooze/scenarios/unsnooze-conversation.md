---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `Z` on a conversation in Snoozed
  kind: actor
  actor: user
  entities:
  - entity: conversation
    effect: reads
    facts:
    - Snoozed until
  contexts:
    tui:
      place: tidemail::snoozed
- text: TideMail ends the snooze and the conversation is back in Waiting on Them
  kind: product
  actor: user
  entities:
  - entity: conversation
    effect: changes
    from: Snoozed
    to: Waiting
    facts:
    - Snoozed until
  contexts:
    tui:
      place: tidemail::snoozed
---

# Unsnooze a conversation early

## Trigger

The person wants to deal with it now.

## Outcome

The conversation waits in Waiting on Them again.
