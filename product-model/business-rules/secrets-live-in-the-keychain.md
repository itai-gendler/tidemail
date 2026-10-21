---
appliesTo:
- type: entity
  id: account
  facts:
  - Password
- type: entity
  id: settings
  facts:
  - AI key
references:
- kind: code
  role: implementation
  target: internal/config/keyring.go
- kind: doc
  role: intent
  target: docs/guide.md
---

# Passwords, OAuth tokens and AI keys are kept in the system keychain

TideMail keeps account passwords, OAuth refresh tokens and AI API keys in libsecret on Linux and Keychain on macOS, loads them at startup and moves them out of the configuration file when Settings is saved. Outbox entries, account summaries and errors never carry them.
