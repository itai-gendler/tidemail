---
appliesTo:
- type: entity
  id: draft
  effect: removes
permits:
- actors:
  - user
- unattended: true
- related:
  - verb: holds
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
  target: internal/mailapp/delivery.go#Deliver
---

# Only the person, TideMail's delivery, or an agent granted Send mail, removes a draft

The person deletes or discards drafts. Delivering a message deletes the draft it came from, whether TideMail delivers it on its own or an agent with Send mail processes the queue.
