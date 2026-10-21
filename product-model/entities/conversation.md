---
domain: waiting-on-them
relations:
- entity: message
  verb: includes
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: internal/ui/waiting.go#computeWaitingWithSnoozes
- kind: code
  role: implementation
  target: internal/db/waiting.go#ListWaitingCandidates
- kind: doc
  role: intent
  target: docs/guide.md
---

# Conversation

A thread of messages linked by their Message-ID, In-Reply-To and References headers, across every account and folder except Trash, Spam and Drafts. Waiting on Them follows the conversations whose latest real message is the person's own and went to someone else.

## Information kept

- **Participants** — everyone who wrote or received a message in it
- **Latest message** — its newest message that is not a draft, a bounce or from a robot
- **Waiting for** — the people the person is waiting to hear from
- **Waiting since** — when the person sent the latest message
- **Snoozed until** — when a snoozed wait comes back

## States

### Waiting

The person's own message is the latest, went to at least one other person, and was sent after TideMail was first set up; the conversation is listed in Waiting on Them.

### Stopped

The person chose Stop waiting for this wait; it stays out of Waiting on Them until the wait ends.

### Snoozed

The wait is hidden from Waiting on Them until its snooze time.

### Answered

Someone else's reply is now the latest message, so nobody is waited for until the person writes again.
