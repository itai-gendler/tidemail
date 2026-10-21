---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `i` while reading a message with blocked remote images
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Body
  contexts:
    tui:
      place: tidemail::message
- text: TideMail fetches the images for this message only and draws them in the reading pane
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

# Load a message's remote images

## Trigger

The person wants to see a message as it was designed.

## Outcome

The message's remote images are shown; other messages stay blocked.
