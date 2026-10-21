---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `d` on a delivered entry in the Outbox
  kind: actor
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail removes the entry from the Outbox
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: removes
    from: Sent
  contexts:
    tui:
      place: tidemail::outbox
---

# Clear a sent entry

## Trigger

The Outbox is cluttered with delivered mail.

## Outcome

The entry is gone; the mail stays in Sent.
