---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `a` in Filters
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail runs every enabled rule over every folder of every account, the first matching rule acting on each message
  kind: product
  actor: user
  entities:
  - entity: filter-rule
    effect: reads
    facts:
    - Account
    - Conditions
    - Action
    - Order
  - entity: message
    effect: changes
    facts:
    - Folder
    - Read
  - entity: account
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::filters
---

# Run every rule over all mail

## Trigger

The person reorganizes all their mail by the rules.

## Outcome

Every cached message that a rule matches is acted on.

## Edge cases

- An account whose settings cannot be resolved is skipped and reported; the others still run.
