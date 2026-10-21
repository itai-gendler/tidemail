---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail messages read cache:123 --json`
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
- text: TideMail returns the cached message with its plain-text and HTML bodies and its account, folder, UID and Message-ID
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - To
    - Cc
    - Subject
    - Date
    - Body
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

# Read a cached message from the command line

## Trigger

A script needs a message's text.

## Outcome

The script has the body as cached; a body never cached comes back empty.

## Edge cases

- A cache id names one row on this computer; it is not an IMAP UID and does not survive a cache rebuild.
