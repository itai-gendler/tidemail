---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person highlights an account and presses Shift+K
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
    - Position
  contexts:
    tui:
      place: tidemail::accounts
- text: TideMail swaps it with the account above and saves the new order
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    facts:
    - Position
  contexts:
    tui:
      place: tidemail::accounts
---

# Move an account up the list

## Trigger

The person wants an account higher in the sidebar and sender picker.

## Outcome

The account appears one place higher everywhere.
