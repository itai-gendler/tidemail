---
type: agent
actors:
- ai-agent
references:
- kind: doc
  role: intent
  target: docs/cli.md
- kind: code
  role: implementation
  target: internal/cli/skills.go#RunInstallSkill
- kind: code
  role: implementation
  target: internal/mailapp/prepare.go#Allowed
---

# Agent skill

How a person's AI agent works with their mail: the TideMail skill installed into the agent tells it to run the mail commands with `--agent`, which checks every command against the capabilities granted in `agent_permissions`. The agent never handles the IMAP or SMTP credentials itself, and sending needs the person's approval of the exact message on every invocation.
