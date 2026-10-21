---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `r` on a failed send in the Outbox
  kind: actor
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Last error
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail queues it again with its tries reset and the current attempt limit, due at once
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: changes
    from: Failed
    to: Queued
    facts:
    - Attempts
    - Attempt limit
    - Next attempt
    - Last error
  - entity: settings
    effect: reads
    facts:
    - Maximum attempts
  contexts:
    tui:
      place: tidemail::outbox
---

# Retry a failed message

## Trigger

The cause of the failure, such as a wrong From address, has been fixed.

## Outcome

The message is delivered from the account as it now stands.

## Edge cases

- Only failed and uncertain messages can be retried; a message being sent says to wait for the attempt to finish.
- A message whose sending account is gone asks for the account to be restored first.
