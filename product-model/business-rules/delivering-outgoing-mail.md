---
appliesTo:
- type: entity
  id: outgoing-message
  effect: changes
permits:
- actors:
  - user
- unattended: true
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

# Only the person, TideMail itself, or an agent granted Send mail, delivers or retries outgoing mail

TideMail delivers due mail on its own while the client runs. The person delivers it with `tidemail outbox process` and retries failures. An AI agent processes the queue or retries a message only while Send mail is granted, and only with `--yes` on the invocation.
