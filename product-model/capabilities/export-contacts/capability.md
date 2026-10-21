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

# Export contacts

Write every contact to a contacts.vcf file in a folder the person chooses (`x` in Contacts).
