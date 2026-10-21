---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+U on a message whose unsubscribe target is an email address
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
- text: TideMail opens compose from the message's account, addressed to that address with the subject it asks for, or unsubscribe
  kind: product
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
---

# Open a prefilled unsubscribe message

## Trigger

The list unsubscribes by email.

## Outcome

A prefilled message waits in compose; sending it is the confirmation.
