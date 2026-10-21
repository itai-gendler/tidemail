---
domain: waiting-on-them
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/waiting.go#undoStopWaiting
- kind: code
  role: implementation
  target: internal/ui/waiting.go#executeWaitingCommand
---

# Resume waiting

Put a stopped conversation back in Waiting on Them: Ctrl+Z right after Stop waiting, or Resume waiting in the command palette.
