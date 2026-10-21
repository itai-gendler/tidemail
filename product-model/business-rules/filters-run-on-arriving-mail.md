---
appliesTo:
- type: entity
  id: filter-rule
- type: capability
  id: sync-mailbox
references:
- kind: code
  role: implementation
  target: internal/ui/filter_runner.go#applyRulesOnArrival
- kind: code
  role: implementation
  target: internal/ui/sync.go#syncMailboxCmdWithMode
---

# Enabled rules run on mail as it arrives

Every sync runs the enabled rules on the messages it just fetched, with no AI call. Mail a rule moved, archived, deleted, sent to spam or marked read is neither counted nor announced as new.
