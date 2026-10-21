---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person has set their own Azure app as the Microsoft client
  kind: condition
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: The person presses Ctrl+O on an Outlook account
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail shows a short code and the address to approve it at, and waits
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: The person approves the code at microsoft.com/devicelogin
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail receives the refresh token and holds it for the form
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
---

# Sign in with a device code through the person's own app

## Trigger

The person registered their own Azure app.

## Outcome

The form holds a completed sign-in, ready to save.
