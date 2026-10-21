---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses F7 in compose
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::compose
- text: Spell check is off in Settings → Editor
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Spell check
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail says spell check needs turning on in Settings → Editor
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::compose
---

# Point to the setting when spell check is off

## Trigger

Spell check is off, as it is by default.

## Outcome

Nothing is checked.
