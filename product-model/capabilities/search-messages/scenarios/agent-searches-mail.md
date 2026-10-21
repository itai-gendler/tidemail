---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail messages search "invoice" --agent --json`
  kind: actor
  actor: ai-agent
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: Message search is granted in Agent permissions
  kind: condition
  entities:
  - entity: agent-permissions
    effect: reads
    facts:
    - Message search
  - entity: message
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: TideMail returns the matching messages' metadata without bodies
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
    - Read
    - Attachments
    - Folder
  contexts:
    agent:
      place: agent-skill
---

# An agent searches cached mail

## Trigger

The agent is asked to find mail.

## Outcome

The agent has the matches and their cache ids.
