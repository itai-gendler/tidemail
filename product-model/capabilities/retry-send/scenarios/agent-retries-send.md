---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail outbox retry 42 --agent --yes --json` after the person approved it
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
- text: TideMail queues it again
  kind: product
  actor: ai-agent
  entities:
  - entity: outgoing-message
    effect: changes
    from: Failed
    to: Queued
    facts:
    - Attempts
    - Next attempt
    - Last error
  contexts:
    agent:
      place: agent-skill
---

# An agent retries a failed send

## Trigger

The person asks the agent to try again.

## Outcome

The message waits for queue processing.
