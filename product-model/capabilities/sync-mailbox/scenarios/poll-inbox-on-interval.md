---
kind: unattended
routes:
  tui: TideMail
steps:
- text: An account's refresh interval of N minutes has passed
  kind: condition
  unattended: true
  entities:
  - entity: account
    effect: reads
    facts:
    - Refresh
  contexts:
    tui:
      place: tidemail::unified-inbox
- text: TideMail syncs the account's inbox
  kind: product
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
- text: TideMail re-reads the account's folder list from the server at most once an hour, adding new folders and dropping vanished ones
  kind: product
  entities:
  - entity: folder
    effect: creates
    facts:
    - Name
    - Parent
    - Kind
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::sidebar
---

# Poll an inbox on its interval

## Trigger

The polling interval of an account comes round.

## Outcome

The inbox is current and folders added or removed on the server appear or disappear.

## Edge cases

- At launch every automatically refreshing account's inbox syncs at once.
- Manual-only accounts never poll and open no push connection.
