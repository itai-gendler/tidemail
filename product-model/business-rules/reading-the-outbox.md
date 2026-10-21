---
appliesTo:
- type: entity
  id: outgoing-message
  effect: reads
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
    fact: Read outbox
    is: Granted
references:
- kind: code
  role: implementation
  target: internal/cli/mail_reads.go#RunMailRead
---

# Only the person, TideMail itself, or an agent granted Read outbox, reads the Outbox

The person and TideMail's own delivery read every outgoing message. An AI agent lists the Outbox and reads one entry's status only while Read outbox (`outbox.read`) is granted, which it is by default. Outbox summaries never include bodies, Bcc recipients or credentials.
