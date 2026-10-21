---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `e` on a failed send in the Outbox
  kind: actor
  actor: user
  entities:
  - entity: outgoing-message
    effect: reads
    facts:
    - Subject
    - Last error
  contexts:
    tui:
      place: tidemail::outbox
- text: TideMail moves it back into Drafts and opens it in compose
  kind: product
  actor: user
  entities:
  - entity: outgoing-message
    effect: removes
    from: Failed
  - entity: draft
    effect: creates
    facts:
    - Sending account
    - To
    - Cc
    - Bcc
    - Subject
    - Body
    - Attachments
    - In reply to
    - Last saved
  contexts:
    tui:
      place: tidemail::compose
---

# Edit a failed message from the Outbox

## Trigger

A failure needs the message itself changed, such as a wrong recipient.

## Outcome

The message is a draft again, open for editing.
