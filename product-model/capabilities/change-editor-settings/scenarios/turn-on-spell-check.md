---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person turns Spell check on and sets the language to Español
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Spell check
    - Spell check language
  contexts:
    tui:
      place: tidemail::editor-settings
- text: The person presses Ctrl+S
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::editor-settings
- text: TideMail saves the settings and underlines misspelled words in compose from then on
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Spell check
    - Spell check language
  contexts:
    tui:
      place: tidemail::editor-settings
---

# Turn on spell check in Spanish

## Trigger

The person writes in Spanish and wants typos caught.

## Outcome

Compose underlines misspellings and F7 steps through them.
