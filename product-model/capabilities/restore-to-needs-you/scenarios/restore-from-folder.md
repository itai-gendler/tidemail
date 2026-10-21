---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person opens the dismissed message outside Needs You and chooses Restore to Needs You in the command palette
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::message
- text: TideMail clears the dismissal, so the message shows in Needs You again while its tags qualify it
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Dismissed from Needs You
  contexts:
    tui:
      place: tidemail::message
---

# Restore a dismissed message from its folder

## Trigger

The person changes their mind later.

## Outcome

The message is back in Needs You.
