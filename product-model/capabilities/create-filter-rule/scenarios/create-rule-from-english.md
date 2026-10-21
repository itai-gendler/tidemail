---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `n` in Filters and picks an account, or All accounts
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::filters
- text: The person types move newsletters from substack to Reading and presses Enter
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail asks the AI provider for a rule, checks it against the account's folders and shows its conditions and action for review
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
  - entity: settings
    effect: reads
    facts:
    - AI provider
  - entity: account
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
- text: TideMail saves the rule at the end of the list, turned on
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
  contexts:
    tui:
      place: tidemail::filters
---

# Create a rule from a description

## Trigger

The person wants some mail handled the same way every time.

## Outcome

The rule runs on new mail as it arrives, with no AI call per message.

## Edge cases

- `e` at the review returns to the description; Esc discards the rule.
