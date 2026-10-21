---
kind: primary
routes:
  tui: TideMail
steps:
- text: The person presses `Z` on a message in Needs You
  kind: actor
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - Subject
  contexts:
    tui:
      place: tidemail::needs-you
- text: The person chooses Tomorrow morning
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::needs-you
- text: TideMail keeps 8:00 AM tomorrow as the message's wake time and takes it out of Needs You
  kind: product
  actor: user
  entities:
  - entity: message
    effect: changes
    facts:
    - Snoozed until
  contexts:
    tui:
      place: tidemail::needs-you
---

# Snooze a message until tomorrow morning

## Trigger

A message needs the person, but not today.

## Outcome

The message is out of Needs You and listed in Snoozed until 8:00 AM tomorrow.

## Edge cases

- Later today is 7:00 PM, or after 5:00 PM three hours after the next full hour; Tomorrow evening is 7:00 PM; This weekend is 9:00 AM Saturday; Next week is 9:00 AM next Monday.
- Every copy of the message, in any folder, shares the snooze.
