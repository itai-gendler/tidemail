---
domain: settings
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/settings.go
- kind: doc
  role: intent
  target: docs/cli.md
---

# Change CLI settings

Change how the interactive `tidemail cli` menu and wizard behave in Settings → CLI. Scripted commands and runs with --json, --agent, --yes or --no-interactive ignore these settings.
