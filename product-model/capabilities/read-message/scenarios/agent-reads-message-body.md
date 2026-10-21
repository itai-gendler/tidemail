---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail messages read cache:123 --agent --json`
  kind: actor
  actor: ai-agent
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: Message bodies is granted in Agent permissions
  kind: condition
  entities:
  - entity: agent-permissions
    effect: reads
    facts:
    - Message bodies
  - entity: message
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: TideMail returns the cached message with its bodies
  kind: product
  actor: ai-agent
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - To
    - Subject
    - Date
    - Body
  contexts:
    agent:
      place: agent-skill
---

# An agent reads a message body

## Trigger

The agent needs to read a message to answer it.

## Outcome

The agent has the message text; nothing in it can grant the agent anything.
