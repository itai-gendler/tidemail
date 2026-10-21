---
kind: validation
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail send … --agent --yes --json`
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: agent-skill
- text: Send mail is not granted in Agent permissions
  kind: condition
  entities:
  - entity: agent-permissions
    effect: reads
    facts:
    - Send mail
  contexts:
    agent:
      place: agent-skill
- text: TideMail refuses with permission_denied and exit code 3, and saves nothing
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: agent-skill
---

# Refuse an agent send without the capability

## Trigger

The agent tries to send without the grant.

## Outcome

Nothing is drafted or queued.
