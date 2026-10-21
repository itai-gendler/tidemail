---
availability:
- place: tidemail
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/ui/messages.go#openedMessageCmd
- kind: code
  role: implementation
  target: internal/ui/content.go
- kind: code
  role: implementation
  target: internal/ui/message_render.go
- kind: code
  role: implementation
  target: internal/cli/mail_reads.go#RunMailRead
- kind: doc
  role: intent
  target: README.md
---

# Read message

Open a message in the reading pane: HTML mail is rendered as terminal text, with receipts kept in columns, newsletter cards kept together and, on terminals that can draw them, embedded images inline. Ctrl+E shows the full headers with SPF, DKIM and DMARC results. From the command line, `tidemail messages read` returns a cached message's plain-text and HTML body.
