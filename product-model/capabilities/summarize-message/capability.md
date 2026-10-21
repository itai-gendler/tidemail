---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/summary.go#openSummary
- kind: code
  role: implementation
  target: internal/ai/ai.go
- kind: code
  role: implementation
  target: internal/db/messages.go#SaveSummary
---

# Summarize message

Ask the configured AI provider for a summary of a message (`` ` ``). TideMail sends the subject and plain-text body, keeps the summary with the message, and shows a kept summary again without a new call; `C` copies it and `M` saves it as a Markdown file.
