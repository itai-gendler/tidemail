---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/snooze.go#unsnoozeCurrent
- kind: code
  role: implementation
  target: internal/ui/snooze.go#expireSnoozesCmd
---

# Unsnooze

End a snooze early (`Z` in Snoozed). Snoozes also end on their own at their wake time, including those that came due while TideMail was closed.
