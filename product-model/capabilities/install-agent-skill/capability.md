---
availability:
- place: command-line
references:
- kind: code
  role: implementation
  target: internal/cli/skills.go#RunInstallSkill
- kind: code
  role: implementation
  target: internal/cli/skills.go#skillDestination
- kind: doc
  role: intent
  target: docs/cli.md
---

# Install agent skill

Install TideMail's skill into an AI agent's personal skills (`tidemail install-skill codex|claude|pi|hermes`), so the agent knows to use the mail commands in agent mode. Only TideMail's own SKILL.md is written, never the agent's other configuration, and an existing one is replaced only with --force.
