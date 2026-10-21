---
domain: compose
references:
- kind: code
  role: implementation
  target: internal/db/drafts.go
- kind: code
  role: implementation
  target: internal/ui/drafts.go#importRemoteDraftsCmd
- kind: doc
  role: context
  target: STATUS.md
---

# Draft

An unsent message kept on this computer under its sending account and listed in that account's Drafts folder. Drafts written elsewhere and found in the server's Drafts folder are copied in, so they can be opened, edited and sent here too.

## Information kept

- **Sending account** — the account it will be sent from
- **To** — the recipients
- **Cc** — the copied recipients
- **Bcc** — the blind-copied recipients
- **Subject** — the subject line
- **Body** — the text being written
- **Attachments** — the files attached so far
- **In reply to** — the message it answers or forwards, which keeps it in that conversation
- **Last saved** — when it was last saved
