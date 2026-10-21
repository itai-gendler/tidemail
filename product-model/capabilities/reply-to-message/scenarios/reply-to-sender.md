---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `r` on a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Subject
  contexts:
    tui:
      place: tidemail::message
- text: 'TideMail opens compose from the account the message arrived on, addressed to the sender or Reply-To address, with Re: on the subject and the original''s readable text quoted'
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Reply-To
    - Subject
    - Body
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
---

# Reply to the sender

## Trigger

The person wants to answer a message.

## Outcome

A reply is ready in compose, kept in the original's conversation.
