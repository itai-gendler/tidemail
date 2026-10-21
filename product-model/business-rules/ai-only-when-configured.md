---
appliesTo:
- type: capability
  id: summarize-message
- type: capability
  id: check-grammar
- type: capability
  id: create-filter-rule
references:
- kind: code
  role: implementation
  target: internal/ai/ai.go#New
---

# AI features run only with a configured provider

Summaries, grammar checks and filter creation send text to the provider chosen in Settings → AI and do nothing until one is configured. A summary sends the subject and plain-text body; a grammar check sends only the person's own text, never the quote; filter creation sends the description and the account's folder names.
