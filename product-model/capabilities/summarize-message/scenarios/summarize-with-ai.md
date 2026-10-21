---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `` ` `` on a message
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::message
- text: TideMail sends the subject and body to the configured AI provider and shows the summary when it returns
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
    - Body
  - entity: settings
    effect: reads
    facts:
    - AI provider
    - AI model
  contexts:
    tui:
      place: tidemail::message
- text: TideMail keeps the summary with the message
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Summary
  contexts:
    tui:
      place: tidemail::message
---

# Summarize a message

## Trigger

The person wants the gist of a long message.

## Outcome

The summary is shown and kept; opening it again needs no AI call.

## Edge cases

- With Mark read after summary on, the message is also marked read.
- `z` shows or hides quoted text, `C` copies and `M` saves a .md file to the summary save folder.
