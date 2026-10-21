---
appliesTo:
- type: capability
  id: run-filter-rules
- type: capability
  id: sync-mailbox
- type: capability
  id: reorder-filter-rules
references:
- kind: code
  role: implementation
  target: internal/ui/filter_runner.go#firstMatch
- kind: code
  role: implementation
  target: internal/filter/filter.go#Matches
---

# The first enabled rule that matches a message acts on it

Rules are tried in list order, limited to the account each applies to; the first enabled one whose conditions match decides the message's action, and later rules are not tried. A rule with no conditions never matches. Text conditions ignore case.
