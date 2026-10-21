---
kind: edge
routes:
  tui: TideMail
steps:
- text: A due outgoing message's sending account is no longer configured
  kind: condition
  unattended: true
  entities:
  - entity: account
    effect: reads
    facts: []
  - entity: outgoing-message
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::outbox
- text: 'TideMail marks it failed: sender account unavailable'
  kind: product
  entities:
  - entity: outgoing-message
    effect: changes
    from: Queued
    to: Failed
    facts:
    - Last error
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::outbox
---

# Fail a message whose account is gone

## Trigger

The account was deleted after the message was queued.

## Outcome

The message waits for the account to be restored, or to be edited and sent from another one.
