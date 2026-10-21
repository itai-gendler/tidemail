---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person highlights an account in Accounts and presses Space
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
  contexts:
    tui:
      place: tidemail::accounts
- text: TideMail saves that account as the default and marks it ★ [default]
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Default account
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::accounts
---

# Mark the default sender

## Trigger

The person sends most new mail from one account.

## Outcome

New messages start from that account, whatever its position or name later becomes.

## Edge cases

- Replies and forwards ignore the default and use the account the message arrived on.
