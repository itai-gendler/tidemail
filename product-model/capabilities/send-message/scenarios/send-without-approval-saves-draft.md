---
kind: alternate
routes:
  cli: Command line
steps:
- text: The person runs `tidemail send` with recipients, subject and body but without --yes
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail saves it as a draft and returns state drafted
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: creates
    facts:
    - Sending account
    - To
    - Subject
    - Body
    - Last saved
  contexts:
    cli:
      place: command-line
---

# Save a draft when delivery is not authorized

## Trigger

A complete scripted send carries no delivery authorization.

## Outcome

Nothing is queued; the draft waits in the client.
