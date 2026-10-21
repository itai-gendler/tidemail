---
appliesTo:
- type: context
  context:
    place: agent-skill
- type: entity
  id: agent-permissions
references:
- kind: code
  role: implementation
  target: internal/mailapp/prepare.go#Allowed
- kind: code
  role: implementation
  target: internal/cli/mail_reads.go#RunMailRead
- kind: doc
  role: intent
  target: docs/cli.md
---

# An agent uses only the capabilities granted in Agent permissions

Every command an agent runs with `--agent` is checked against `agent_permissions`: listing accounts needs Read accounts, listing messages Message metadata, searching Message search, reading a body Message bodies, saving a draft Create drafts, reading the Outbox Read outbox, and queueing, processing, retrying or cancelling mail Send mail. A command without its capability is refused with exit code 3. Without the setting, every capability but Message bodies and Send mail is granted; an empty list grants none.

## Rationale

The agent skill gives guidance, not credentials or standing approval. The checks are a command-line policy, not an operating-system sandbox for an agent with unrestricted shell access.
