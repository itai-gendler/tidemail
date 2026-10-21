---
domain: accounts
availability:
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/cli/mail_reads.go#RunMailRead
- kind: doc
  role: intent
  target: docs/cli.md
---

# List accounts

List the configured accounts with their ids, names, sender addresses and which one is the default (`tidemail accounts list`). Passwords and tokens are never included.
