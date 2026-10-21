---
domain: compose
references:
- kind: code
  role: implementation
  target: internal/mailtemplate/mailtemplate.go#Load
- kind: doc
  role: intent
  target: docs/guide.md
---

# Template

A canned reply to insert while writing: one of six built-ins (Thanks, Got it, Out of office, Propose a meeting, Polite decline, Follow up) or a `.md` or `.txt` file in the templates folder next to the configuration, which replaces a built-in of the same name.

## Information kept

- **Name** — unique, taken from the file name
- **Subject** — an optional subject, set only when the message has none yet
- **Body** — the text, with {first_name}, {name}, {my_name} and {date} filled in when it is used
