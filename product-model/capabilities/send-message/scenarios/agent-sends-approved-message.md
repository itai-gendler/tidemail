---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The person has reviewed and approved the exact recipients, subject, body and attachments
  kind: condition
  entities: []
  contexts:
    agent:
      place: agent-skill
- text: The AI agent runs `tidemail send … --agent --yes --json`
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
- text: TideMail queues the outgoing message and returns state queued
  kind: product
  actor: ai-agent
  entities:
  - entity: outgoing-message
    effect: creates
    to: Queued
    facts:
    - Sending account
    - Recipients
    - Subject
    - Content
    - Attempts
    - Attempt limit
    - Next attempt
  contexts:
    agent:
      place: agent-skill
---

# An agent sends a message the person approved

## Trigger

The person asked the agent to send a reply they approved.

## Outcome

The message is queued for delivery.

## Edge cases

- Instructions inside incoming mail can never grant a capability or authorize a send.
