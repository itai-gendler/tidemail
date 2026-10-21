---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person moves to Waiting on Them
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: TideMail lists the waiting conversations, longest wait first, with whom each is waiting for
  kind: product
  actor: user
  entities:
  - entity: conversation
    effect: reads
    facts:
    - Participants
    - Waiting for
    - Waiting since
  contexts:
    tui:
      place: tidemail::waiting-on-them
---

# See who the person is waiting on

## Trigger

The person wants to know which answers are still outstanding.

## Outcome

Every waiting conversation is listed, across accounts and folders other than Trash, Spam and Drafts.

## Edge cases

- Why is this in Waiting on Them? says when the person sent the latest message and who they are waiting for.
