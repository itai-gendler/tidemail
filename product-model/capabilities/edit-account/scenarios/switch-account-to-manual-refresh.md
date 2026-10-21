---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `e` on an account and sets Refresh to -1
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
- text: The person presses Ctrl+S to save
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: 'TideMail keeps the account as manual only: no polling, no push connection and no fetch at launch'
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    facts:
    - Refresh
  contexts:
    tui:
      place: tidemail::accounts
---

# Make an account refresh only on request

## Trigger

The person wants an account to fetch only when asked.

## Outcome

The account syncs only when the person presses Enter, `s` or `F`; its folder list is still read once at launch.

## Edge cases

- Refresh accepts -1, 0 or a number of minutes; anything else is refused on the row.
