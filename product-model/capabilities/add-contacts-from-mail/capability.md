---
domain: contacts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/contact_manager.go#addPickedContacts
- kind: code
  role: implementation
  target: internal/db/contacts.go#SeenAddresses
---

# Add contacts from mail

Turn addresses found in synced mail into contacts (`f` in Contacts): TideMail lists the senders and recipients of cached mail that are not contacts yet, filtered as the person types.
