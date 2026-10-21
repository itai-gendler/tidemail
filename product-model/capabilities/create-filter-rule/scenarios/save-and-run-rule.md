---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `r` at the review instead of Enter
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail saves the rule and runs it over the inboxes of the accounts it applies to
  kind: product
  actor: user
  entities:
  - entity: filter-rule
    effect: creates
    to: Enabled
    facts:
    - Description
    - Account
    - Conditions
    - Action
    - Target folder
    - Order
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
---

# Save a rule and run it at once

## Trigger

The person wants mail already in the inbox handled too.

## Outcome

The rule is saved and the inbox mail it matches is already filed.

## Edge cases

- `a` at the review saves it and runs every enabled rule over all mail in every folder.
