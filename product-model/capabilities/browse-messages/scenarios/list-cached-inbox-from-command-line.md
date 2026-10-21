---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail messages list --unread --limit 25 --json`
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
- text: TideMail reads the cached Unified Inbox and returns one page of message metadata, with cache ids, account, folder and the offset of the next page
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
    - To
    - Folder
  - entity: account
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
---

# List the cached inbox from the command line

## Trigger

A script wants the unread inbox.

## Outcome

The script has up to 25 unread messages' metadata and knows whether more pages follow.

## Edge cases

- Results never include bodies; the limit is 1 to 1000, 50 by default.
- Nothing connects to the server; mail is only as current as the client's last sync.
