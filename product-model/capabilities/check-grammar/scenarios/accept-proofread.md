---
kind: primary
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
- text: TideMail sends the person's own text, without the quote, to the AI provider and previews the corrected version
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - Body
  - entity: settings
    effect: reads
    facts:
    - AI provider
    - AI model
  contexts:
    tui:
      place: tidemail::compose
- text: The person presses `y`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail replaces the text with the corrected one, keeps the quote below it and saves the draft
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: changes
    facts:
    - Body
    - Last saved
  contexts:
    tui:
      place: tidemail::compose
---

# Accept a proofread

## Trigger

The person wants their wording checked before sending.

## Outcome

The draft holds the corrected text.
