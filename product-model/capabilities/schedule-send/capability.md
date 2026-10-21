---
domain: compose
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/schedule_send.go#queueScheduledSend
- kind: code
  role: implementation
  target: internal/ui/schedule_send.go#scheduleChoiceTime
---

# Schedule send

Send a finished message later (Schedule send in compose's command palette): in one hour, tomorrow at 9:00, next Monday at 9:00, or a date and time picked on a calendar. The time is kept in the Outbox, so it survives a restart.
