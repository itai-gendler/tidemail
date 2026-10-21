---
kind: edge
routes:
  tui: TideMail
steps:
- text: The person describes a rule and presses Enter
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::filters
- text: No AI provider is configured, or it fails or returns something that is not a valid rule
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - AI provider
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail shows the error and saves nothing
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::filters
---

# Fail when no AI provider can build the rule

## Trigger

The rule cannot be built.

## Outcome

No rule is added; the person can configure AI or try other words.
