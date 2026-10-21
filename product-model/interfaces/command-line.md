---
type: cli
actors:
- user
entryPoints:
- cli: tidemail send
- cli: tidemail cli
references:
- kind: doc
  role: intent
  target: docs/cli.md
- kind: code
  role: implementation
  target: internal/cli/mail.go#RunHeadless
- kind: code
  role: implementation
  target: internal/cli/interactive.go#composeInteractive
---

# Command line

The `tidemail` mail commands for shell scripts and pipes, and the guided `tidemail cli` menu and compose wizard. They use the same accounts, credentials, drafts, cache and outbox as the client, read only cached mail, and return a versioned JSON result when asked.
