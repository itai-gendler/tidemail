---
domain: filters
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/filter_manager.go#reorderRule
---

# Reorder filter rules

Move a rule up or down the list (Shift+K / Shift+J in Filters). Rules are tried in this order and the first one that matches a message acts on it.
