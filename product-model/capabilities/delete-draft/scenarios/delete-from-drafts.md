---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `d` on a draft in Drafts
  kind: actor
  actor: user
  entities:
  - entity: draft
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::drafts
- text: TideMail deletes its server copy, if it came from the server, then the draft
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: removes
  contexts:
    tui:
      place: tidemail::drafts
---

# Delete a draft from Drafts

## Trigger

A draft is no longer needed.

## Outcome

The draft is gone here and from the server's Drafts folder.
