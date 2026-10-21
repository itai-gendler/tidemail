---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `d` on a rule
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
- text: TideMail deletes it
  kind: product
  actor: user
  entities:
  - entity: filter-rule
    effect: removes
    from: Enabled
  contexts:
    tui:
      place: tidemail::filters
---

# Delete a rule

## Trigger

A rule is no longer wanted.

## Outcome

The rule is gone; mail it already filed stays where it is.
