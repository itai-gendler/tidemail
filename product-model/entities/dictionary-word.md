---
references:
- kind: code
  role: implementation
  target: internal/db/spell_words.go#ListSpellWords
- kind: code
  role: implementation
  target: internal/ui/spell_dictionary.go
---

# Dictionary word

A word the person added to the offline spell check's personal dictionary, so it is never flagged again.

## Information kept

- **Word** — the word, kept in lower case
