---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses `a` on a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::message-list
- text: The account has no folder flagged or named as an archive
  kind: condition
  entities:
  - entity: folder
    effect: reads
    facts:
    - Kind
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail says archive failed because no archive folder was found and leaves the message where it is
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts: []
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::message-list
---

# Refuse to archive without an Archive folder

## Trigger

The account's server has no Archive folder.

## Outcome

Nothing moves; the person can move the message instead.
