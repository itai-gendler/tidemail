---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `r` on an enabled rule
  kind: actor
  actor: user
  entities:
  - entity: filter-rule
    effect: reads
    facts:
    - Description
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail matches the rule against the cached inbox mail of its accounts and applies its action to each match on the server
  kind: product
  actor: user
  entities:
  - entity: filter-rule
    effect: reads
    facts:
    - Account
    - Conditions
    - Action
    - Target folder
  - entity: message
    effect: changes
    facts:
    - Folder
    - Read
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail reports how many messages matched and how many it acted on
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::filters
---

# Run one rule over its inboxes

## Trigger

Mail that arrived before the rule existed should be handled too.

## Outcome

The matching inbox mail is filed, marked read, archived, deleted or sent to spam.

## Edge cases

- A spam action uses the account's Junk folder, creating one named Junk if there is none.
- A delete moves to Trash, or deletes for good where there is no Trash.
