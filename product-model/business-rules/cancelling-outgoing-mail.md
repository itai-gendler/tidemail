---
appliesTo:
- type: entity
  id: outgoing-message
  effect: removes
permits:
- actors:
  - user
- related:
  - verb: sends
    entity: account
  - verb: owns
    entity: user
  - verb: connects
    entity: ai-agent
  when:
  - entity: agent-permissions
    fact: Send mail
    is: Granted
references:
- kind: code
  role: implementation
  target: internal/cli/mail.go#runOutboxAction
---

# Only the person, or an agent granted Send mail, takes a message out of the Outbox

The person cancels a queued or failed message and clears delivered ones. An AI agent cancels a queued message only while Send mail is granted, with `--yes`.
