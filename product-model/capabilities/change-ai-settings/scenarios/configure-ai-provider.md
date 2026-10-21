---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person chooses Claude in Settings → AI, picks a model and pastes the API key
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - AI provider
    - AI model
  contexts:
    tui:
      place: tidemail::ai-settings
- text: The person presses Ctrl+S
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::ai-settings
- text: TideMail saves the provider and model, puts the key in the keychain and turns the AI tools on
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - AI provider
    - AI model
    - AI key
  contexts:
    tui:
      place: tidemail::ai-settings
---

# Configure an AI provider

## Trigger

The person wants summaries, grammar checks and plain-English filters.

## Outcome

The AI tools work with the chosen provider.
