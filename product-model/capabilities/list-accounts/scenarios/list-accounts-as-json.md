---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail accounts list --json`
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
- text: TideMail returns each account's id, name and sender address, marking the default one
  kind: product
  actor: user
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
    - From address
    - Email / login
  - entity: settings
    effect: reads
    facts:
    - Default account
  contexts:
    cli:
      place: command-line
---

# List accounts for a script

## Trigger

A script needs an account id to send from.

## Outcome

The script has every account's id; `--account` accepts the id or an unambiguous name.
