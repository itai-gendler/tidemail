---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/snooze.go#snoozePresets
- kind: code
  role: implementation
  target: internal/ui/snooze.go#parseCustomSnooze
- kind: code
  role: implementation
  target: internal/db/snooze.go#SetSnooze
- kind: doc
  role: intent
  target: docs/guide.md
---

# Snooze

Hide something from Needs You or Waiting on Them until later (`Z`, or Snooze in the command palette). In Waiting on Them it snoozes the conversation; elsewhere it snoozes messages, every selected one to the same time. Snoozing is local: it creates no folder, moves nothing and leaves read state and tags alone.
