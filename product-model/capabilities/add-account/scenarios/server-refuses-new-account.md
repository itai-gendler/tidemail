---
kind: edge
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+S on a filled-in account form
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: The IMAP server refuses the login or cannot be reached
  kind: condition
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail shows the connection error, with any password left out of it, and keeps the form open
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
---

# Keep nothing when the server refuses

## Trigger

The details are wrong or the server is down.

## Outcome

No account is added; the person can correct the form and save again.
