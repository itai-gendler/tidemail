---
appliesTo:
- type: entity
  id: account
  facts:
  - Refresh
- type: capability
  id: sync-mailbox
references:
- kind: code
  role: implementation
  target: internal/ui/sync.go#syncPollInterval
- kind: code
  role: implementation
  target: internal/ui/sync.go#syncsAutomatically
---

# An account's Refresh decides whether its inbox syncs on its own

Refresh 0 keeps a push connection open with a safety poll every 30 minutes; N polls every N minutes; -1 never fetches on its own, not even at launch, though its folder list is still read once at launch.
