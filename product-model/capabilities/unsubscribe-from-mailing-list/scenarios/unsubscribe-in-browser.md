---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+U and confirms
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
- text: The unsubscribe target is a web link without one-click support
  kind: condition
  entities: []
  contexts:
    tui:
      place: tidemail::message
- text: TideMail opens the link in the browser
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message
---

# Unsubscribe on the sender's page

## Trigger

The sender offers a web page to unsubscribe.

## Outcome

The unsubscribe page is open in the browser; if it cannot open, its address stays on the status line.
