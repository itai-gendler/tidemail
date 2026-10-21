---
domain: settings
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/settings.go
- kind: code
  role: implementation
  target: internal/config/config.go#NormalizeSendMaxAttempts
---

# Change editor settings

Change how compose and sending behave in Settings → Editor: standard or Vim keys, spell check and its language, the send delay and the maximum delivery attempts.
