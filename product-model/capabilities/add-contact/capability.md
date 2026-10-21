---
domain: contacts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/contact_manager.go#submitForm
- kind: code
  role: implementation
  target: internal/db/contacts.go#AddContactWithMetadata
---

# Add contact

Save someone as a contact (`n` in Contacts). An address that is already a contact updates that contact instead of adding a second one.
