---
kind: person
acts: external
relations:
- entity: account
  verb: owns
  cardinality: one-to-many
- entity: ai-agent
  verb: connects
  cardinality: one-to-many
references:
- kind: doc
  role: intent
  target: README.md
---

# User

The person using TideMail on their own computer. There is no sign-in to TideMail itself: whoever runs it uses every configured account, its cache and its outbox.
