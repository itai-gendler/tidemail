---
kind: alternate
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
- text: The person chooses the Gmail provider, which fills in Google's servers, and enters the full address and an app password
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
- text: TideMail connects to Gmail with the app password and lists its labels
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail keeps the account with Auth on App password, its password in the keychain, and adds Gmail's labels, including Sent Mail, All Mail and Spam
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

# Add a Gmail account with an app password

## Trigger

The person adds a Gmail, Yahoo or iCloud account, all of which take an app password.

## Outcome

The account is saved and signs in to IMAP and SMTP with the app password.

## Edge cases

- Google sign-in with OAuth is unavailable while TideMail's Google app awaits approval, so the Gmail form asks for an app password; Gmail accounts already signed in with OAuth stay as they are.
