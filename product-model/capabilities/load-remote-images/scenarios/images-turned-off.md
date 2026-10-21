---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person presses `i` while reading a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Body
  contexts:
    tui:
      place: tidemail::message
- text: Images is set to Off
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Images
  contexts:
    tui:
      place: tidemail::message
- text: TideMail says image display is off and keeps the text placeholders
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message
---

# Refuse while images are off

## Trigger

The person has turned images off.

## Outcome

Nothing is fetched.

## Edge cases

- On terminals that cannot draw images, such as foot and WezTerm, every image stays a labelled text placeholder.
