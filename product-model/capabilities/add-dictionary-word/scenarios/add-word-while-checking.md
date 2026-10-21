---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `a` on a flagged name while checking spelling
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail adds the word to the personal dictionary and stops flagging it
  kind: product
  actor: user
  entities:
  - entity: dictionary-word
    effect: creates
    facts:
    - Word
  contexts:
    tui:
      place: tidemail::compose
---

# Add a flagged word while checking

## Trigger

A correct word, such as a name or jargon, is flagged.

## Outcome

The word is never flagged again.
