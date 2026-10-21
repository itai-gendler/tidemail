---
domain: compose
availability:
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/cli/mail.go#runComposeCLI
- kind: code
  role: implementation
  target: internal/mailapp/prepare.go#SaveDraft
- kind: doc
  role: intent
  target: docs/cli.md
---

# Create draft

Save a draft from the command line (`tidemail draft create`), with the body from text, a file, Markdown, a template or a pipe, and attachments. The draft is kept under the chosen account, or the default one, and is opened and sent from the client.
