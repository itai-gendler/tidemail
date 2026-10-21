---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail outbox process --agent --yes --json`
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: agent-skill
- text: Send mail is granted in Agent permissions
  kind: condition
  entities:
  - entity: agent-permissions
    effect: reads
    facts:
    - Send mail
  contexts:
    agent:
      place: agent-skill
- text: TideMail delivers each due outgoing message and deletes its draft
  kind: product
  actor: ai-agent
  entities:
  - entity: outgoing-message
    effect: changes
    from: Queued
    to: Sent
    facts:
    - Attempts
    - Content
  - entity: draft
    effect: removes
  contexts:
    agent:
      place: agent-skill
---

# An agent processes the approved queue

## Trigger

The agent's approved send must go out without the client.

## Outcome

The due mail is delivered.

## Edge cases

- Without --yes, agent processing is refused with approval_required.
