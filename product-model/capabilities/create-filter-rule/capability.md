---
domain: filters
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/filter_manager.go#handleFilterReview
- kind: code
  role: implementation
  target: internal/ui/filter_runner.go#generateFilterCmd
- kind: code
  role: implementation
  target: internal/ui/filter_runner.go#prepareFilterFoldersCmd
- kind: code
  role: implementation
  target: internal/filter/parse.go
- kind: code
  role: implementation
  target: internal/filter/generate.go
---

# Create filter rule

Build a filter rule from plain English (Manage filters in the command palette, then `n`). The person picks the account it applies to, or all accounts, and describes the rule; the configured AI provider turns it into conditions and an action once, checked against the account's folders, and the person reviews it before saving. Saving puts it at the end of the list, turned on.
