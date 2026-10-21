---
kind: unattended
routes:
  tui: TideMail
steps:
- text: A sync stores a message from one of the person's own addresses, sent after TideMail was first set up, as the newest in its thread
  kind: condition
  unattended: true
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - To
    - Date
  contexts:
    tui:
      place: tidemail::waiting-on-them
- text: TideMail lists the conversation in Waiting on Them, waiting for the other people in it
  kind: product
  entities:
  - entity: conversation
    effect: creates
    to: Waiting
    facts:
    - Participants
    - Latest message
    - Waiting for
    - Waiting since
  contexts:
    tui:
      place: tidemail::waiting-on-them
---

# Start a wait when the person's own mail is synced

## Trigger

The person's message is now the latest in a conversation.

## Outcome

The conversation waits in Waiting on Them until someone else replies.

## Edge cases

- After a send, TideMail syncs that account's Sent folder, so the stored copy starts the wait.
- Mail only to the person's own addresses, or only to robots and mailing lists, starts no wait.
- On a new install, mail sent before TideMail was set up never starts a wait.
