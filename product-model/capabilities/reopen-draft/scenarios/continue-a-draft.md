---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person opens an account's Drafts folder
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  - entity: draft
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::drafts
- text: TideMail copies in drafts from the server's Drafts folder it has not seen before and lists the account's drafts
  kind: product
  actor: user
  entities:
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
  - entity: account
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::drafts
- text: The person presses Enter on a draft
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
- text: TideMail opens it in compose from its sending account
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
---

# Continue a saved draft

## Trigger

The person wants to finish a message started earlier, here or elsewhere.

## Outcome

The draft is open in compose and keeps saving as the person types.

## Edge cases

- A draft copied from the server that was already copied in is never overwritten by the server's version.
