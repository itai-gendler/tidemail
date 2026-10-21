---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses Space on a disabled rule
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
- text: TideMail turns it on
  kind: product
  actor: user
  entities:
  - entity: filter-rule
    effect: changes
    from: Disabled
    to: Enabled
    facts: []
  contexts:
    tui:
      place: tidemail::filters
---

# Turn a rule on

## Trigger

A rule is needed again.

## Outcome

The rule runs on new mail and in manual runs.
