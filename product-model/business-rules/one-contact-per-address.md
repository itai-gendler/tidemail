---
appliesTo:
- type: entity
  id: contact
  effect: creates
references:
- kind: code
  role: implementation
  target: internal/db/contacts.go#AddContactWithMetadata
---

# Each email address is one contact

Adding or importing an address that is already a contact updates that contact instead of adding a second one; a detail left blank keeps the one already saved.
