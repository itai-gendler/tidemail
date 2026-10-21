---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `O`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail lists the outgoing messages, unsent ones first, newest first, with each one's state and tries
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Subject
    - Attempts
    - Attempt limit
  contexts:
    tui:
      place: tidemail::outbox
- text: The person moves to a failed send
  kind: actor
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Sending account
    - Recipients
    - Last error
  contexts:
    tui:
      place: tidemail::outbox
---

# Inspect the Outbox

## Trigger

The status bar reports a failed send, or the person wants to see what is on its way.

## Outcome

The person sees each message's state, its sender and recipients, and why the last attempt failed.

## Edge cases

- The status bar keeps reporting failed and unconfirmed sends, with how long they have waited, until nothing in the Outbox needs the person; a message inside its undo window is not reported.
- The Outbox row's badge counts only the sends that need the person.
