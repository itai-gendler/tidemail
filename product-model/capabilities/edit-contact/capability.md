---
domain: contacts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/contact_manager.go#beginEdit
- kind: code
  role: implementation
  target: internal/db/contacts.go#UpdateContactWithMetadata
---

# Edit contact

Change a contact's details (`e` in Contacts).
