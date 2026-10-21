---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail accounts list --agent --json`
  kind: actor
  actor: ai-agent
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: Read accounts is granted in Agent permissions
  kind: condition
  entities:
  - entity: agent-permissions
    effect: reads
    facts:
    - Read accounts
  - entity: account
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: TideMail returns each account's id, name, sender address and whether it is the default
  kind: product
  actor: ai-agent
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
    - From address
    - Email / login
  - entity: settings
    effect: reads
    facts:
    - Default account
  contexts:
    agent:
      place: agent-skill
---

# An agent lists the accounts

## Trigger

The agent needs to know which accounts it can draft from.

## Outcome

The agent has the account list, without any credentials.
