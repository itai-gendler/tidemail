---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Space on an enabled rule
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
- text: TideMail turns it off
  kind: product
  actor: user
  entities:
  - entity: filter-rule
    effect: changes
    from: Enabled
    to: Disabled
    facts: []
  contexts:
    tui:
      place: tidemail::filters
---

# Turn a rule off

## Trigger

A rule should pause.

## Outcome

The rule is kept but never runs.
