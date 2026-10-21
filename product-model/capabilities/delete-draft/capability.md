---
domain: compose
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/drafts.go#deleteDraftCmd
- kind: code
  role: implementation
  target: internal/ui/drafts.go#discardComposeDraft
---

# Delete draft

Remove a draft: `d` on it in the Drafts folder, or discard while closing compose. A draft copied from the server is deleted on the server first, so it does not come back on the next sync.
