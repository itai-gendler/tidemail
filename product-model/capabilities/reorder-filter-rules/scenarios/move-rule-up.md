---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Shift+K on a rule
  kind: actor
  actor: user
  entities:
  - entity: filter-rule
    effect: reads
    facts:
    - Description
    - Order
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail swaps it with the rule above
  kind: product
  actor: user
  entities:
  - entity: filter-rule
    effect: changes
    facts:
    - Order
  contexts:
    tui:
      place: tidemail::filters
---

# Move a rule up

## Trigger

A more specific rule should win over a broader one.

## Outcome

The rule is tried before the one it passed.
