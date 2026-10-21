---
kind: system
acts: external
references:
- kind: doc
  role: intent
  target: docs/cli.md
- kind: code
  role: implementation
  target: internal/cli/skills.go#RunSkill
---

# AI agent

An AI agent the person runs (Codex, Claude Code, Pi, Hermes or another) that has the TideMail skill installed and works with their mail through the command line in agent mode, within the capabilities they grant.
