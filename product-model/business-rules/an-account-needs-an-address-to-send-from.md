---
appliesTo:
- type: entity
  id: account
  facts:
  - From address
  - Email / login
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#validateAccountForConnect
---

# Every account has an address to send from

An account's From address must hold an email address, optionally with a name. It may be blank only when the login is itself an address; the named providers require a full address as the login.
