---
kind: validation
routes:
  cli: Command line
steps:
- text: The person runs `tidemail send --to me@example.com --body "Hi" --yes` without a subject
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail refuses it as incomplete, with exit code 2, and queues nothing
  kind: product
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
---

# Refuse an authorized send without a subject

## Trigger

An authorized send lacks a subject, or both body and attachments.

## Outcome

Nothing is saved or queued.
