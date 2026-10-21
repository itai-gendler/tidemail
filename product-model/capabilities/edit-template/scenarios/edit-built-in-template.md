---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `e` on the Out of office template, changes the text and presses Ctrl+S
  kind: actor
  actor: user
  entities:
  - entity: template
    effect: reads
    facts:
    - Name
    - Body
  contexts:
    tui:
      place: tidemail::compose
- text: TideMail saves the person's own copy under the same name, which replaces the built-in from now on
  kind: product
  actor: user
  entities:
  - entity: template
    effect: changes
    facts:
    - Body
  contexts:
    tui:
      place: tidemail::compose
---

# Edit a built-in template

## Trigger

A built-in template does not fit how the person writes.

## Outcome

The person's version is offered in its place, in compose and on the command line.
