---
appliesTo:
- type: capability
  id: snooze
- type: capability
  id: unsnooze
references:
- kind: code
  role: implementation
  target: internal/db/snooze.go
---

# Snoozing changes nothing on the server

A snooze creates no folder, moves nothing, leaves read state and tags alone, and is kept as an absolute time on this computer. A dismissal or a Stop waiting still applies after a snooze ends.
