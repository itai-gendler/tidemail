---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail outbox list --agent --json`
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: agent-skill
- text: Read outbox is granted in Agent permissions
  kind: condition
  entities:
  - entity: agent-permissions
    effect: reads
    facts:
    - Read outbox
  contexts:
    agent:
      place: agent-skill
- text: TideMail returns the outgoing messages' states and summaries
  kind: product
  actor: ai-agent
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Recipients
    - Subject
    - Attempts
    - Next attempt
    - Last error
  contexts:
    agent:
      place: agent-skill
---

# An agent reads the Outbox

## Trigger

The agent checks on a message it queued.

## Outcome

The agent can report whether it was delivered.
