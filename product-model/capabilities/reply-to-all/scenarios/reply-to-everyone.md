---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+R on a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - To
    - Cc
  contexts:
    tui:
      place: tidemail::message
- text: TideMail opens compose with the sender in To and the other recipients in Cc, without any of the person's own addresses
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Reply-To
    - To
    - Cc
    - Subject
    - Body
  - entity: account
    effect: reads
    facts:
    - From address
    - Email / login
  contexts:
    tui:
      place: tidemail::compose
---

# Reply to everyone

## Trigger

The person wants everyone on the thread to see the answer.

## Outcome

A reply-all is ready in compose.
