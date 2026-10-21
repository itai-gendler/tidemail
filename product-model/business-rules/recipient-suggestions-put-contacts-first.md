---
appliesTo:
- type: entity
  id: contact
- type: capability
  id: compose-message
references:
- kind: code
  role: implementation
  target: internal/db/contacts.go#AutocompleteAddresses
---

# Recipient suggestions put saved contacts before addresses from mail

To, Cc and Bcc suggest saved contacts first, then addresses found in synced mail that are not contacts yet.
