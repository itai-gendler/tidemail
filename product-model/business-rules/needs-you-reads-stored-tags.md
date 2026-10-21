---
appliesTo:
- type: capability
  id: dismiss-from-needs-you
- type: capability
  id: restore-to-needs-you
- type: capability
  id: browse-messages
references:
- kind: code
  role: implementation
  target: internal/db/attention.go#AttentionOf
- kind: code
  role: implementation
  target: internal/ui/needs_you.go
---

# Needs You comes only from tags already stored

Needs You lists inbox messages tagged as needing a reply, urgent or important, by any plugin, installed or since removed, or by the person's own correction. Opening it never runs a plugin or goes online. A dismissal or a snooze keeps a message out whatever its tags say.
