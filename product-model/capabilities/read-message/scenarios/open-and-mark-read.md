---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Enter on a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Subject
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail shows the message in the reading pane
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - To
    - Cc
    - Subject
    - Date
    - Body
    - Attachments
  contexts:
    tui:
      place: tidemail::message
- text: Mark read on open is on
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Mark read on open
  contexts:
    tui:
      place: tidemail::message
- text: TideMail marks the message read on the server, then in the cache
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Read
  contexts:
    tui:
      place: tidemail::message
---

# Open a message and mark it read

## Trigger

The person wants to read a message.

## Outcome

The message is shown and counted as read everywhere, including other clients.

## Edge cases

- With Mark read on focus on, resting the cursor on a message is enough.
- Remote images stay blocked until the person loads them.
- Ctrl+E shows or hides the full headers and authentication results.
