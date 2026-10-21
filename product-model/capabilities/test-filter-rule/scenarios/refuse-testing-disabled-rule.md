---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses `t` on a disabled rule
  kind: actor
  actor: user
  entities:
  - entity: filter-rule
    effect: reads
    facts:
    - Description
  contexts:
    tui:
      place: tidemail::filters
- text: TideMail says the rule is disabled and that Space enables it
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::filters
---

# Refuse to test a disabled rule

## Trigger

The rule is off.

## Outcome

Nothing is counted.
