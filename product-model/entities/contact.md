---
domain: contacts
references:
- kind: code
  role: implementation
  target: internal/db/contacts.go#AddContactWithMetadata
- kind: code
  role: implementation
  target: internal/ui/contact_manager.go
---

# Contact

A saved person to write to, one per email address, suggested first when addressing mail and exchanged with other apps as vCard.

## Information kept

- **Email** — the address; each address is one contact
- **Name** — the display name
- **Phone** — a phone number
- **Organization** — where they work
- **Title** — their job title
- **Note** — a free note
