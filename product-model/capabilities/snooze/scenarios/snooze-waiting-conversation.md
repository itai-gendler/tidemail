---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `Z` on a conversation in Waiting on Them and picks Next week
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
- text: TideMail keeps 9:00 AM next Monday as its wake time and takes it out of Waiting on Them
  kind: product
  actor: user
  entities:
  - entity: conversation
    effect: changes
    from: Waiting
    to: Snoozed
    facts:
    - Snoozed until
  contexts:
    tui:
      place: tidemail::waiting-on-them
---

# Snooze a waiting conversation

## Trigger

The person will chase an answer next week.

## Outcome

The conversation is in Snoozed until then; a reply ends the snooze at once.
