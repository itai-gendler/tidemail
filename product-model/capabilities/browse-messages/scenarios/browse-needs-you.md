---
kind: alternate
routes:
  tui: TideMail
steps:
- text: The person moves to Needs You
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::sidebar
- text: 'TideMail lists the inbox messages tagged as needing a reply, urgent or important, read or not, leaving out dismissed and snoozed ones: urgent first, then needing a reply, then important, newest first within each'
  kind: product
  actor: user
  entities:
  - entity: message
    effect: reads
    facts:
    - From
    - Subject
    - Date
    - Read
    - Starred
    - Attachments
    - Tags
    - Dismissed from Needs You
    - Snoozed until
  contexts:
    tui:
      place: tidemail::needs-you
---

# See what needs the person

## Trigger

The person wants the mail that still needs doing.

## Outcome

Needs You lists it, most pressing first; its count is how many there are, read or not.

## Edge cases

- Without a plugin that tags mail, Needs You stays empty and says Nothing needs your attention.
- Opening Needs You only reads stored tags; it never runs a plugin or goes online.
- Why is this in Needs You? in the command palette lists the reasons and the tags behind them.
