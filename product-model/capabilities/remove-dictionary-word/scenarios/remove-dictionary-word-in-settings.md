---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `d` on a word in Personal dictionary
  kind: actor
  actor: user
  entities:
  - entity: dictionary-word
    effect: reads
    facts:
    - Word
  contexts:
    tui:
      place: tidemail::editor-settings
- text: TideMail removes it, and the spell check flags it again
  kind: product
  actor: user
  entities:
  - entity: dictionary-word
    effect: removes
  contexts:
    tui:
      place: tidemail::editor-settings
---

# Remove a word from the dictionary

## Trigger

A word was added by mistake.

## Outcome

The word is no longer in the personal dictionary.
