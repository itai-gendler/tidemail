---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person moves to the Unified Inbox
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail lists every account's cached inbox mail together, each message tinted with its account's color
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Subject
    - Date
    - Read
    - Starred
    - Attachments
  - entity: account
    effect: reads
    facts:
    - Color
  contexts:
    tui:
      place: tidemail::unified-inbox
---

# Browse the Unified Inbox

## Trigger

The person wants all incoming mail in one list.

## Outcome

Every inbox's mail is in one list.
