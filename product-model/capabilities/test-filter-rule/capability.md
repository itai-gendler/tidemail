---
domain: filters
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/filter_manager.go#runSelectedRule
- kind: code
  role: implementation
  target: internal/ui/filter_runner.go#applyRulesCmd
---

# Test filter rule

See what one rule would do without changing anything (`t` in Filters): TideMail counts the messages it matches in the inboxes of the accounts it applies to.
