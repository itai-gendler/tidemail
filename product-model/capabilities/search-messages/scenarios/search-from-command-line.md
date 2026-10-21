---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail messages search "invoice" --json`
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
- text: TideMail searches the cached messages and returns one page of matching metadata
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - To
    - Subject
    - Date
    - Read
    - Attachments
    - Folder
  contexts:
    cli:
      place: command-line
---

# Search cached mail from the command line

## Trigger

A script looks for mail about a subject.

## Outcome

The script has the matches' metadata and cache ids for `messages read`.
