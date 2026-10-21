---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person opens Personal dictionary in Settings → Editor, presses `a` and types a word of letters, apostrophes or hyphens
  kind: actor
  actor: user
  entities:
  - entity: dictionary-word
    effect: reads
    facts:
    - Word
  - entity: settings
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::editor-settings
- text: TideMail adds the word; the change applies at once
  kind: product
  actor: user
  entities:
  - entity: dictionary-word
    effect: creates
    facts:
    - Word
  contexts:
    tui:
      place: tidemail::editor-settings
---

# Add a word in Settings

## Trigger

The person wants a word accepted before it is ever flagged.

## Outcome

The word is in the personal dictionary.
