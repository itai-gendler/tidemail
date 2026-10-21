---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses Esc in compose and answers `d` to discard
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
- text: TideMail deletes the draft and closes compose
  kind: product
  actor: user
  entities:
  - entity: draft
    effect: removes
  contexts:
    tui:
      place: tidemail::compose
---

# Discard a draft when closing compose

## Trigger

The person gives up on a message.

## Outcome

Nothing of it is kept.

## Edge cases

- Clearing everything from a draft and closing compose deletes it without asking.
