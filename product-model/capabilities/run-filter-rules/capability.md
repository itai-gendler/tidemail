---
domain: filters
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/filter_runner.go#applyRulesCmd
- kind: code
  role: implementation
  target: internal/ui/filter_runner.go#firstMatch
- kind: code
  role: implementation
  target: internal/ui/filter_apply.go#applyFilterAction
---

# Run filter rules

Apply rules to mail already in TideMail: `r` runs the highlighted rule over the inboxes of the accounts it applies to, and `a` runs every enabled rule over all mail in every folder. Each message gets the action of the first enabled rule, in list order, that matches it.
