---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+U on a message with no unsubscribe header or labelled link
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
  contexts:
    tui:
      place: tidemail::message
- text: TideMail says there is no unsubscribe link in this message
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message
---

# Say so when there is no unsubscribe option

## Trigger

The message offers no way to unsubscribe.

## Outcome

Nothing is sent or opened.
