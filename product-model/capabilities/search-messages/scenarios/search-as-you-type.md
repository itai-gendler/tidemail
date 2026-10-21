---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `/` and types a word
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::message-list
- text: TideMail lists the cached messages from every account whose subject, sender, recipients or body match, updating as the person types
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - To
    - Subject
    - Body
    - Date
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::search-results
---

# Search all cached mail as the person types

## Trigger

The person is looking for a message.

## Outcome

The matching messages are listed; the search row stays while the person reads them.

## Edge cases

- Search reaches only cached mail.
- Several `#tags` must all match, and they combine with words: invoice #billing finds billing mail that mentions an invoice.
- A corrected tag counts, so a recategorized message is found under its new tag.
