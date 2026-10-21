---
domain: compose
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/compose.go#NewCompose
- kind: code
  role: implementation
  target: internal/ui/model.go#handleCompose
- kind: code
  role: implementation
  target: internal/ui/drafts.go#saveDraftCmd
- kind: code
  role: implementation
  target: internal/db/contacts.go#AutocompleteAddresses
---

# Compose

Start a new message (`c`, or `c` on selected contacts in Contacts). It starts from the default account, and TideMail saves it as a draft under the sending account as the person types. With more than one account the From row is an account picker; the chosen account's SMTP server, From address and signature go with it. To, Cc and Bcc suggest saved contacts first, then addresses found in synced mail.
