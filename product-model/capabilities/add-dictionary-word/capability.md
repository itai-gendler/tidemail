---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/spell.go#updateSpell
- kind: code
  role: implementation
  target: internal/ui/spell.go#persistSpellWords
- kind: code
  role: implementation
  target: internal/ui/spell_dictionary.go#handleSpellDictionaryKey
- kind: code
  role: implementation
  target: internal/db/spell_words.go#AddSpellWord
---

# Add dictionary word

Teach the spell check a word: `a` on a flagged word while checking, or `a` in Settings → Editor → Personal dictionary. Words are kept in TideMail's database.
