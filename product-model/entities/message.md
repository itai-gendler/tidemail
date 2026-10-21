---
references:
- kind: code
  role: implementation
  target: internal/db/messages.go
- kind: code
  role: implementation
  target: internal/ui/sync.go#storeFetchedMessages
- kind: code
  role: implementation
  target: internal/db/attention.go
---

# Message

One email in a folder, as TideMail has cached it from the server. The cache serves speed and search; the read state, star and folder belong to the server.

## Information kept

- **From** — the sender's name and address
- **To** — the recipients
- **Cc** — the copied recipients
- **Reply-To** — where replies go when the sender asks for another address
- **Subject** — the subject line
- **Date** — when it was sent
- **Body** — the plain-text and HTML body
- **Attachments** — the attached files and embedded images
- **Authentication results** — the full headers, with SPF, DKIM and DMARC results
- **Read** — whether it has been read; the server's \Seen flag
- **Starred** — the server's \Flagged star
- **Folder** — the folder that holds it
- **Summary** — the AI summary made for it, kept once made
- **Tags** — needs reply, urgency, importance and category, from installed plugins' annotations and the person's own corrections
- **Dismissed from Needs You** — kept out of Needs You whatever its tags say
- **Snoozed until** — when it comes back to Needs You; shared by every copy of the message
