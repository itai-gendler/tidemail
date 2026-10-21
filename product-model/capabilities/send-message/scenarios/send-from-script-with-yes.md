---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail send --to me@example.com --subject "Hello" --body "Hi" --yes --json`
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail checks the input, adds the default account's signature and queues the outgoing message, due after the send delay, returning state queued
  kind: product
  actor: user
  entities:
  - entity: account
    effect: reads
    facts:
    - From address
    - Signature
  - entity: settings
    effect: reads
    facts:
    - Default account
    - Send delay
  - entity: outgoing-message
    effect: creates
    to: Queued
    facts:
    - Sending account
    - Recipients
    - Subject
    - Content
    - Attempts
    - Attempt limit
    - Next attempt
  contexts:
    cli:
      place: command-line
---

# Queue a send from a script

## Trigger

A script reports something by mail.

## Outcome

The message is queued; it leaves when the client or `tidemail outbox process` runs, so queued is not yet sent.

## Edge cases

- A pipe can supply the body; `--markdown` renders a Markdown file; `--attach` repeats.
- `--dry-run` checks and builds the message without saving or queueing anything.
