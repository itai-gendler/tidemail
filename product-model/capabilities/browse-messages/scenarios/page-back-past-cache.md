---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person moves down past the last cached message in a folder
  kind: actor
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
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail fetches the next 100 older messages from the server and adds them to the list
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
  contexts:
    tui:
      place: tidemail::message-list
---

# Fetch older mail past the end of the list

## Trigger

The person wants mail older than what is cached.

## Outcome

The older mail is listed and searchable; paging continues as far back as the server goes.
