---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+T on the account form
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail connects to the IMAP server with the form's details and reports how many folders it found; nothing is saved
  kind: product
  actor: user
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
---

# Report a working connection

## Trigger

The person wants to know the details work before saving.

## Outcome

The status line confirms the connection and the folder count.
