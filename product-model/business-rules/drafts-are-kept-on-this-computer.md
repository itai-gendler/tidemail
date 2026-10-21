---
appliesTo:
- type: entity
  id: draft
- type: capability
  id: reopen-draft
references:
- kind: code
  role: implementation
  target: internal/ui/drafts.go#saveDraftCmd
- kind: code
  role: implementation
  target: internal/ui/drafts.go#importRemoteDraftsCmd
- kind: doc
  role: context
  target: STATUS.md
---

# Drafts are kept on this computer

A draft is saved locally under its sending account as the person types and listed in that account's Drafts folder; it is not uploaded to the server. Drafts found in the server's Drafts folder are copied in once and never overwritten by the server's version afterwards, and deleting one deletes the server's copy first.
