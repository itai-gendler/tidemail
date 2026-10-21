---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The send delay is 0
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Send delay
  contexts:
    tui:
      place: tidemail::compose
- text: The person presses Ctrl+S in compose
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - To
    - Subject
    - Body
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail queues the outgoing message as due now and starts delivering it straight away
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: creates
    to: Queued
    facts:
    - Sending account
    - Recipients
    - Subject
    - Content
    - Attempts
    - Attempt limit
    - Next attempt
  contexts:
    tui:
      place: tidemail::compose
---

# Send at once with no delay

## Trigger

The person wants mail to leave immediately.

## Outcome

Delivery starts at once, with no window to undo.
