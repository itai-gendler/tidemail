---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person opens Settings with `S`, moves to Display and turns Mouse support on
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Mouse support
  contexts:
    tui:
      place: tidemail::display-settings
- text: The person presses Ctrl+S
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::display-settings
- text: TideMail saves the settings and applies them
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Mouse support
  contexts:
    tui:
      place: tidemail::display-settings
---

# Turn on mouse support

## Trigger

The person wants to click rows and scroll with the wheel.

## Outcome

Clicks, double-clicks, the wheel and right-click menus work; the terminal's own click-drag selection does not while it is on.

## Edge cases

- Esc on the section list, or `q`, leaves Settings without saving.
