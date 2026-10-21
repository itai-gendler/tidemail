---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+L on a Custom account whose domain's mail is handled by Google Workspace
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail finds Google in the domain's MX records and switches the form to the Gmail provider, with its servers and sign-in options
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
---

# Switch to a built-in provider from the domain's MX

## Trigger

The domain's mail is hosted by Google, Microsoft 365, iCloud or Yahoo.

## Outcome

The form uses that provider's servers and sign-in rules.

## Edge cases

- Ctrl+L replaces whatever the host rows hold; changing or clearing the address removes only settings its earlier lookup filled in.
