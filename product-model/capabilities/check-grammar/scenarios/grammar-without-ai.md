---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+G in compose
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - Body
  contexts:
    tui:
      place: tidemail::compose
- text: No AI provider is configured
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - AI provider
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail says AI is not configured and that `S` opens Settings
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
---

# Point to Settings when no AI provider can proofread

## Trigger

AI is off.

## Outcome

The text is unchanged and nothing is sent anywhere.

## Edge cases

- With nothing written but the quote, it says there is nothing to check.
