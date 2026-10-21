---
appliesTo:
- type: capability
  id: send-message
- type: capability
  id: create-draft
references:
- kind: code
  role: implementation
  target: internal/cli/mail.go#runComposeCLI
- kind: doc
  role: intent
  target: docs/cli.md
---

# A command-line send without authorization only saves a draft

`tidemail send` queues mail only when the invocation carries `--yes` or the person approves the review in the wizard; otherwise it saves a draft. Approval is never read from a piped body, and an authorized send needs recipients, a subject and a body or attachment.
