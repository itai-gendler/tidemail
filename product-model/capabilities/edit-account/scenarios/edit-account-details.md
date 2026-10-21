---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `e` on an account in Accounts
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
- text: The person changes the From address and the signature
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: The person presses Ctrl+S to save
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail connects to the IMAP server again, then keeps the new details
  kind: product
  actor: user
  entities:
  - entity: account
    effect: changes
    facts:
    - From address
    - Signature
  contexts:
    tui:
      place: tidemail::accounts
---

# Change an account's From address and signature

## Trigger

The person wants mail from this account to go out under a different address or signature.

## Outcome

New messages, and every later attempt to deliver a queued one, use the new details.

## Edge cases

- Renaming an account keeps its cached mail, drafts and queued mail, which follow its id, not its name.
