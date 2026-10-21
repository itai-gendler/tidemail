---
domain: filters
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/filter_manager.go#handleFilterList
- kind: code
  role: implementation
  target: internal/db/rules.go#DeleteRule
---

# Delete filter rule

Remove a rule from the list (`d` in Filters).
