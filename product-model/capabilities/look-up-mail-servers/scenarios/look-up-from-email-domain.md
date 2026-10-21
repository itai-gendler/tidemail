---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person types an address on a Custom account's Email / login row and moves to the next row
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: Both host rows are still empty
  kind: condition
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail looks up the domain's SRV records and autoconfig file in the background
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail fills in the IMAP and SMTP rows with the servers it can reach securely and says where they came from
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
---

# Fill in servers from the email domain

## Trigger

The person adds an account at their own mail domain.

## Outcome

The server rows are filled in for the person to check before saving.

## Edge cases

- When the autoconfig file names a login that is not the address, the login row takes it and the address moves to From address.
