---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `X` on a message in Needs You
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
    - Tags
  contexts:
    tui:
      place: tidemail::needs-you
- text: TideMail marks it dismissed, takes it out of Needs You and lowers the count
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

# Dismiss a message from Needs You

## Trigger

A tagged message does not actually need the person.

## Outcome

The message is out of Needs You; its mail, tags and folder are unchanged.

## Edge cases

- A dismissal still applies after a snooze on the message ends.
