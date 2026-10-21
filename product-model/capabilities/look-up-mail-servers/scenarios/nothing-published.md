---
kind: edge
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+L on a Custom account
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: The domain publishes no usable SRV, MX or autoconfig settings
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail says on the status line that nothing was found and leaves the server rows as they were
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
---

# Say so when the domain publishes nothing

## Trigger

The domain has no published mail settings.

## Outcome

The person enters the servers by hand.
