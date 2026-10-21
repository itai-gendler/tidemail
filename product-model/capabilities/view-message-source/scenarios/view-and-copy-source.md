---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Ctrl+O on a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::message
- text: TideMail fetches the raw message from the server and shows it, leaving its read state alone
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Read
  contexts:
    tui:
      place: tidemail::message
- text: The person presses `c`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message
- text: TideMail copies the whole source to the clipboard
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message
---

# View and copy the source

## Trigger

The person needs the exact headers or MIME structure.

## Outcome

The source is on the clipboard and the message is still unread if it was.
