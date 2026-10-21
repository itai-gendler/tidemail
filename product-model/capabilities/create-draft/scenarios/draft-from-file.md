---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail draft create --to ann@example.com --subject "Follow-up" --body-file response.md --attach notes.pdf --json`
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
- text: TideMail checks the recipients and saves the draft under the default account, returning state drafted and its id
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
    - Attachments
    - Last saved
  - entity: settings
    effect: reads
    facts:
    - Default account
  - entity: account
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
---

# Save a draft with a body file and an attachment

## Trigger

A script prepares a message for the person to finish.

## Outcome

The draft is in the account's Drafts folder in the client.

## Edge cases

- Only one body source is accepted; a second is refused with exit code 2.
- `draft create` cannot authorize delivery: --yes, --send-now and --preview are refused.
