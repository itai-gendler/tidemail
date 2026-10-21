---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+U while reading a newsletter
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
- text: TideMail asks for confirmation, showing the site the unsubscribe goes to
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
  contexts:
    tui:
      place: tidemail::message
- text: The person confirms with `y`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message
- text: The sender supports one-click unsubscribe
  kind: condition
  entities: []
  contexts:
    tui:
      place: tidemail::message
- text: TideMail sends the one-click request in the background and says unsubscribed
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message
---

# Unsubscribe with one click

## Trigger

The person no longer wants a newsletter.

## Outcome

The sender has the unsubscribe request without a browser being opened.
