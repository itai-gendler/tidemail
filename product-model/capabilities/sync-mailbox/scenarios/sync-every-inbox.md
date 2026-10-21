---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `s` on the Unified Inbox
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::unified-inbox
- text: TideMail fetches new mail for every account's inbox and adds it to the Unified Inbox
  kind: product
  actor: user
  entities:
  - entity: message
    effect: creates
    facts:
    - From
    - To
    - Cc
    - Reply-To
    - Subject
    - Date
    - Body
    - Attachments
    - Authentication results
    - Read
    - Starred
    - Folder
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::unified-inbox
---

# Sync every inbox from the Unified Inbox

## Trigger

The person wants every inbox current at once.

## Outcome

Each account's inbox is synced.
