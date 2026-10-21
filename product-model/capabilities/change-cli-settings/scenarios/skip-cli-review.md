---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person turns Skip review step on in Settings → CLI and presses Ctrl+S
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Skip review step
  contexts:
    tui:
      place: tidemail::cli-settings
- text: TideMail saves the setting
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Skip review step
  contexts:
    tui:
      place: tidemail::cli-settings
---

# Skip the wizard's review step

## Trigger

The person sends quickly from the wizard and relies on the undo countdown.

## Outcome

The wizard goes from attachments to the countdown; it still shows review for dry runs, agent runs, invalid messages and sends with no delay.
