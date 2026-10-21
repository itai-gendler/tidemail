---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person sets Send delay to 10 seconds and Maximum attempts to 1 in Settings → Editor
  kind: actor
  actor: user
  entities:
  - entity: settings
    effect: reads
    facts:
    - Send delay
    - Maximum attempts
  contexts:
    tui:
      place: tidemail::editor-settings
- text: The person presses Ctrl+S
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::editor-settings
- text: TideMail saves the settings
  kind: product
  actor: user
  entities:
  - entity: settings
    effect: changes
    facts:
    - Send delay
    - Maximum attempts
  contexts:
    tui:
      place: tidemail::editor-settings
---

# Change the send delay and retries

## Trigger

The person wants longer to undo and no automatic retries.

## Outcome

New messages wait 10 seconds and a failed delivery waits for the person instead of retrying.

## Edge cases

- Queued messages keep the attempt limit they were queued with until they are retried.
