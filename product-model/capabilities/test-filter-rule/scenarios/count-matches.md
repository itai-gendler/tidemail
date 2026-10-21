---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `t` on an enabled rule
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
- text: TideMail matches only this rule against the cached mail in its accounts' inboxes and reports how many messages match
  kind: product
  actor: user
  entities:
  - entity: filter-rule
    effect: reads
    facts:
    - Account
    - Conditions
  - entity: message
    effect: reads
    facts:
    - From
    - To
    - Cc
    - Subject
    - Body
    - Attachments
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::filters
---

# Count a rule's matches

## Trigger

The person wants to check a rule before trusting it.

## Outcome

The match count is shown; no mail moves.
