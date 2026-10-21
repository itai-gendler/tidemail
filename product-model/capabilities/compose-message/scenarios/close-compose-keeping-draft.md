---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses Esc in compose with something written
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail asks whether to keep the draft or discard it
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
- text: The person presses `y`
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail saves the draft and closes compose
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: changes
    facts:
    - Body
    - Last saved
  contexts:
    tui:
      place: tidemail::drafts
---

# Close compose and keep the draft

## Trigger

The person stops writing for now.

## Outcome

The draft is listed in the account's Drafts folder; compose with nothing in it closes without asking.
