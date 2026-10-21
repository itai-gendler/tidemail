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

# Enable filter rule

Turn a rule back on (Space on a disabled rule in Filters).
