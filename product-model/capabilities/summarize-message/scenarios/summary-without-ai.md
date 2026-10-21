---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses `` ` `` on a message without a kept summary
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
    - Summary
  contexts:
    tui:
      place: tidemail::message
- text: No AI provider is configured
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - AI provider
  contexts:
    tui:
      place: tidemail::message
- text: TideMail says AI is not configured and that `S` opens Settings
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message
---

# Point to Settings when no AI provider can summarize

## Trigger

AI is off.

## Outcome

Nothing is sent anywhere.
