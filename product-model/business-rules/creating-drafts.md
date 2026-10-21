---
appliesTo:
- type: entity
  id: draft
  effect: creates
permits:
- actors:
  - user
- related: &id001
  - verb: holds
    entity: account
  - verb: owns
    entity: user
  - verb: connects
    entity: ai-agent
  when:
  - entity: agent-permissions
    fact: Create drafts
    is: Granted
- related: *id001
  when:
  - entity: agent-permissions
    fact: Send mail
    is: Granted
references:
- kind: code
  role: implementation
  target: internal/cli/mail.go#runComposeCLI
- kind: code
  role: implementation
  target: internal/cliform/compose.go
---

# Only the person, or an agent granted Create drafts or Send mail, creates drafts

The person's drafts come from compose, the command line and the server's Drafts folder. An AI agent saves a draft only while Create drafts (`drafts.create`) is granted, which it is by default; cancelling a queued send, which turns it back into a draft, needs Send mail.
