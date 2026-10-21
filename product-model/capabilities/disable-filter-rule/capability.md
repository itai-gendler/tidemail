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
  target: internal/db/rules.go#SetRuleEnabled
---

# Disable filter rule

Turn a rule off without deleting it (Space on an enabled rule in Filters).
