---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person presses `T` and moves through the themes, each previewed as it is highlighted
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Theme
  contexts:
    tui:
      place: tidemail::themes
- text: The person presses Enter on one
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::themes
- text: TideMail applies and saves the theme
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Theme
  contexts:
    tui:
      place: tidemail::themes
---

# Pick a theme

## Trigger

The person wants a different look.

## Outcome

The theme is applied everywhere and kept.

## Edge cases

- match-omarchy follows the current Omarchy desktop theme and repaints when it changes.
