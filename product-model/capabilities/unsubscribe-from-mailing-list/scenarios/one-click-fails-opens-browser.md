---
kind: edge
routes:
  tui: TideMail
steps:
- text: The person confirms an unsubscribe from a sender that supports one-click
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
- text: The sender's server refuses the one-click request or does not answer
  kind: condition
  entities: []
  contexts:
    tui:
      place: tidemail::message
- text: TideMail says one-click failed and opens the unsubscribe page in the browser instead
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message
---

# Fall back to the browser when one-click fails

## Trigger

The one-click request did not go through.

## Outcome

The person can finish the unsubscribe on the sender's page.
