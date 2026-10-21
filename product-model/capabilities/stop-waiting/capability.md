---
domain: waiting-on-them
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/waiting.go#stopWaitingCurrent
- kind: code
  role: implementation
  target: internal/db/waiting.go#SetWaitingStopped
---

# Stop waiting

Stop tracking a conversation in Waiting on Them (`X`, or Stop waiting in the command palette). It applies to the current wait only and never changes mail or tags.
