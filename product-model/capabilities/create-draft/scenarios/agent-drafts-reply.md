---
kind: primary
routes:
  agent: Agent skill
steps:
- text: The AI agent runs `tidemail draft create --to ann@example.com --subject "Reply" --body-file response.md --agent --json`
  kind: actor
  actor: ai-agent
  entities:
  - entity: draft
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: Create drafts is granted in Agent permissions
  kind: condition
  entities:
  - entity: agent-permissions
    effect: reads
    facts:
    - Create drafts
  - entity: draft
    effect: reads
    facts: []
  contexts:
    agent:
      place: agent-skill
- text: TideMail saves the draft and returns its id
  kind: product
  actor: ai-agent
  entities:
  - entity: draft
    effect: creates
    facts:
    - Sending account
    - To
    - Subject
    - Body
    - Last saved
  contexts:
    agent:
      place: agent-skill
---

# An agent drafts a reply

## Trigger

The agent prepares an answer for the person to review.

## Outcome

The draft waits in the client; nothing is sent.
