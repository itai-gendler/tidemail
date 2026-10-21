---
kind: edge
routes:
  tui: TideMail
steps:
- text: The person presses `` ` `` on a message
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
- text: The AI provider is unreachable or rejects the request within 30 seconds
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - AI provider
  contexts:
    tui:
      place: tidemail::message
- text: TideMail shows the error in the summary window and keeps nothing
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message
---

# Show the provider's error

## Trigger

The provider is down or the key is wrong.

## Outcome

No summary is kept; the person can try again.
