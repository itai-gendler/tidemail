---
appliesTo:
- type: entity
  id: conversation
  effect: creates
- type: capability
  id: stop-waiting
references:
- kind: code
  role: implementation
  target: internal/ui/waiting.go#computeWaitingWithSnoozes
- kind: code
  role: implementation
  target: internal/db/waiting.go#WaitingSince
---

# A wait starts only from the person's own latest message to someone else

A conversation waits when its newest real message comes from one of the person's configured addresses (display names don't count) and went to at least one other person. Mail between the person's own addresses, mail only to robots or lists, drafts and bounces start nothing, and Trash, Spam and Drafts are ignored. On a new install only mail sent after TideMail was set up can start a wait.
