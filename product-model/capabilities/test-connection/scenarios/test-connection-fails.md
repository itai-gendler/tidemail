---
kind: edge
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
- text: The server refuses the login or cannot be reached
  kind: condition
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail shows the connection error with the password left out
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
---

# Report why the connection failed

## Trigger

The details are wrong or the server is unreachable.

## Outcome

The form stays as it was, with the reason on the status line.
