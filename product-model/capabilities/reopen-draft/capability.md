---
domain: compose
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/drafts.go#importRemoteDraftsCmd
- kind: code
  role: implementation
  target: internal/ui/compose.go#NewComposeFromDraft
---

# Reopen draft

Continue a draft (Enter on it in the account's Drafts folder). Drafts written in webmail or another client and found in the server's Drafts folder are copied in first, so they open here too.
