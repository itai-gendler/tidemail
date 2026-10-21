---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `a` in Accounts
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::accounts
- text: The person keeps the Custom provider and fills in the name, email or login, password, server rows, From address and signature
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
- text: TideMail checks every row, then connects to the IMAP server and lists its folders
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail keeps the account last in the list, puts its password in the system keychain and adds its folders to the sidebar
  kind: product
  actor: user
  entities:
  - entity: account
    effect: creates
    facts:
    - Provider
    - Name
    - Email / login
    - Password
    - Auth
    - IMAP server
    - SMTP server
    - From address
    - Signature
    - Color
    - Refresh
    - Position
  - entity: folder
    effect: creates
    facts:
    - Name
    - Parent
    - Kind
    with: account
  contexts:
    tui:
      place: tidemail::accounts
---

# Add a Custom account

## Trigger

The person wants to read and send mail from another account.

## Outcome

The account is in the list and in the sidebar with its server folders, ready to sync.

## Edge cases

- Leaving a port blank takes the standard one.
- A display name another account already uses is allowed; the form only notes it.
