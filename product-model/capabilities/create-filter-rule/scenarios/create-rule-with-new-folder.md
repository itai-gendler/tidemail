---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person describes a rule for All accounts that files mail somewhere new
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail shows the rule with a notice that saving will create the folder in every account
  kind: product
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::filters
- text: The person presses Enter to save
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail creates the folder in each account that lacks it, then saves the rule
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: creates
    facts:
    - Name
    - Parent
    - Kind
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
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::filters
---

# Create a rule that files into a new folder

## Trigger

The destination folder is new.

## Outcome

The folder exists everywhere the rule applies, and the rule is saved.

## Edge cases

- If a folder cannot be created, the rule is not saved.
