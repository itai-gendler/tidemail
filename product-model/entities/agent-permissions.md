---
singleton: true
references:
- kind: code
  role: implementation
  target: internal/mailapp/prepare.go#Allowed
- kind: doc
  role: intent
  target: docs/cli.md
---

# Agent permissions

The capabilities the person grants AI agents, set as `agent_permissions` in the configuration file. Without the setting, agents may read accounts, list and search message metadata, create drafts and read the Outbox; an empty list grants nothing.

## Information kept

- **Read accounts** — `accounts.read`: list the configured accounts; granted by default
- **Message metadata** — `messages.metadata`: list cached messages without their bodies; granted by default
- **Message search** — `messages.search`: search cached messages; granted by default
- **Message bodies** — `messages.read`: read a cached message's full body; not granted by default
- **Create drafts** — `drafts.create`: save drafts; granted by default
- **Read outbox** — `outbox.read`: list the Outbox and one entry's status; granted by default
- **Send mail** — `mail.send`: queue, process, retry and cancel outgoing mail; not granted by default
