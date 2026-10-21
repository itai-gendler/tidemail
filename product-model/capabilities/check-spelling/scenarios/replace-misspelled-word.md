---
kind: primary
routes:
  tui: TideMail
steps:
- text: Spell check is on
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Spell check
    - Spell check language
  contexts:
    tui:
      place: tidemail::compose
- text: The person presses F7 in compose
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail highlights the first misspelled word with suggestions, the likeliest first
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - Body
  contexts:
    tui:
      place: tidemail::compose
- text: The person presses Enter on a suggestion
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail replaces the word, moves to the next one and saves the draft
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

# Replace a misspelled word

## Trigger

The person wants to fix typos before sending.

## Outcome

The misspelling is corrected; `s` skips a word and `i` ignores it until restart.

## Edge cases

- Nothing is sent anywhere; Ctrl+G is the separate AI grammar check.
