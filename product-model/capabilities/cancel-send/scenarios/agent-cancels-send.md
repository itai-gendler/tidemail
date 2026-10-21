---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail outbox cancel 42 --agent --yes --json`
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
- text: TideMail moves it back to Drafts
  kind: product
  actor: ai-agent
  entities:
  - entity: outgoing-message
    effect: removes
    from: Queued
  - entity: draft
    effect: creates
    facts:
    - Sending account
    - To
    - Cc
    - Bcc
    - Subject
    - Body
    - Attachments
    - In reply to
    - Last saved
  contexts:
    agent:
      place: agent-skill
---

# An agent cancels a queued send

## Trigger

The person tells the agent not to send after all.

## Outcome

The message is a draft again.
