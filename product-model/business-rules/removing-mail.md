---
appliesTo:
- type: entity
  id: message
  effect: removes
permits:
- actors:
  - user
- unattended: true
---

# Only the person and TideMail itself delete mail; agents never do

Messages leave the cache when the person deletes them or TideMail's sync finds them gone from the server.
