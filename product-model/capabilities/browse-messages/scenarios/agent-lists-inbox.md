---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail messages list --agent --json`
  kind: actor
  actor: ai-agent
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: Message metadata is granted in Agent permissions
  kind: condition
  entities:
  - entity: agent-permissions
    effect: reads
    facts:
    - Message metadata
  - entity: message
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: TideMail returns one page of cached inbox metadata without bodies
  kind: product
  actor: ai-agent
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Subject
    - Date
    - Read
    - Starred
    - Attachments
    - To
    - Folder
  contexts:
    agent:
      place: agent-skill
---

# An agent lists the cached inbox

## Trigger

The agent is asked what came in.

## Outcome

The agent has the inbox metadata to work from.
