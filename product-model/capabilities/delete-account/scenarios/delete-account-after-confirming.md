---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `d` on an account in Accounts
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
- text: The person confirms with `y`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::accounts
- text: TideMail removes the account from its configuration and drops its cached folders and messages
  kind: product
  actor: user
  entities:
  - entity: account
    effect: removes
  - entity: folder
    effect: removes
    with: account
  - entity: message
    effect: removes
    with: folder
  contexts:
    tui:
      place: tidemail::accounts
---

# Delete an account after confirming

## Trigger

The person no longer wants an account in TideMail.

## Outcome

The account is gone from the list and the sidebar; its server mail is unchanged.

## Edge cases

- When the deleted account was the default sender, new messages start from the first account again.
- If dropping the cached mail fails, the configuration is put back as it was.
