---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person keeps the Auth row on OAuth for an Outlook account and presses Ctrl+O
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail copies Microsoft's sign-in address to the clipboard and opens the Code row
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: The person signs in and approves in the browser, then pastes the address of the page it lands on into the Code row and presses Enter
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail exchanges the code for a refresh token and holds it for the form
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
---

# Sign in by pasting the browser's redirect

## Trigger

Microsoft no longer accepts passwords for Outlook and Microsoft 365 mailboxes.

## Outcome

The form holds a completed sign-in; saving the account sets its Auth to OAuth and keeps the refresh token in the keychain.

## Edge cases

- Pasting only the code= value works as well.
- Microsoft 365 work and school mailboxes need IMAP enabled by an administrator.
