---
domain: settings
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/spell_dictionary.go#handleSpellDictionaryKey
- kind: code
  role: implementation
  target: internal/db/spell_words.go#RemoveSpellWord
---

# Remove dictionary word

Take a word out of the personal dictionary (`d` in Settings → Editor → Personal dictionary).
