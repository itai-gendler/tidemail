---
appliesTo:
- type: entity
  id: message
  effect: changes
permits:
- actors:
  - user
- unattended: true
references:
- kind: code
  role: implementation
  target: internal/mailapp/prepare.go#Allowed
---

# Only the person and TideMail itself change mail; agents never do

Read state, stars, moves, archives and filter actions come from the person's actions and from TideMail's own sync and filter runs. No agent capability changes a message.
