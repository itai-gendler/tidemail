---
domain: contacts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/contact_manager.go#confirmFilePicker
- kind: code
  role: implementation
  target: internal/db/contacts_vcard.go#ImportVCard
---

# Import contacts

Add contacts from a vCard file (`i` in Contacts): names, addresses, phone numbers, organizations, titles and notes.
