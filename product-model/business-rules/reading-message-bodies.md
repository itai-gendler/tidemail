---
appliesTo:
- type: entity
  id: message
  effect: reads
  facts:
  - Body
permits:
- actors:
  - user
- unattended: true
- related:
  - verb: contains
    entity: folder
  - verb: has
    entity: account
  - verb: owns
    entity: user
  - verb: connects
    entity: ai-agent
  when:
  - entity: agent-permissions
    fact: Message bodies
    is: Granted
references:
- kind: code
  role: implementation
  target: internal/cli/mail_reads.go#RunMailRead
---

# Only the person, TideMail itself, or an agent granted Message bodies, reads a message body

The person reads bodies in the reading pane and with `tidemail messages read`; TideMail reads them to match filter rules and to ask for summaries the person requests. An AI agent reads a body only while Message bodies (`messages.read`) is granted, which it is not by default; listing and searching return metadata only.
