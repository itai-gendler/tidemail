---
kind: primary
result: achieved
routes:
  tui: TideMail
steps:
- text: The person presses Enter on a draft in Drafts
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - Subject
    - To
  contexts:
    tui:
      place: tidemail::drafts
  capability: reopen-draft
- text: TideMail opens the draft in compose from its sending account
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - Sending account
    - To
    - Cc
    - Bcc
    - Subject
    - Body
    - Attachments
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
  capability: reopen-draft
- text: The person presses Ctrl+S
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - To
    - Subject
    - Body
  contexts:
    tui:
      place: tidemail::compose
  capability: send-message
- text: TideMail queues it as an outgoing message for the send delay
  kind: product
  actor: user
  entities:
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
    tui:
      place: tidemail::compose
  capability: send-message
---

# Reopen a draft and send it

## Trigger

A message was left unfinished.

## Outcome

The message leaves after the send delay.
