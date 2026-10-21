---
appliesTo:
- type: entity
  id: outgoing-message
  effect: creates
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
  target: internal/cli/mail.go#runComposeCLI
- kind: code
  role: implementation
  target: internal/mailapp/prepare.go#Allowed
---

# Only the person, or an agent granted Send mail, queues outgoing mail

The person queues mail from compose and the command line. An AI agent queues mail only while Send mail (`mail.send`) is granted in Agent permissions, and every agent send also needs the person's approval of that exact message on the same invocation (`--yes` or an approved review).

## Rationale

Permission to read or draft never authorizes sending, and nothing inside incoming mail can grant it.
