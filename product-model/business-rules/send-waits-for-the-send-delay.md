---
appliesTo:
- type: capability
  id: send-message
- type: capability
  id: cancel-send
- type: capability
  id: schedule-send
references:
- kind: code
  role: implementation
  target: internal/ui/send_undo.go#handleSendQueued
- kind: code
  role: implementation
  target: internal/mailapp/delivery.go#Enqueue
---

# An outgoing message waits for the send delay before it leaves

A message is queued due after the send delay, 5 seconds by default, during which Ctrl+Z, the Outbox or the command line can still take it back into Drafts. A delay of 0 sends at once. A scheduled message waits until its chosen time; `--send-now` on the command line skips the delay.
