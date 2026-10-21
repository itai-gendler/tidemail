---
kind: unattended
routes:
  tui: TideMail
steps:
- text: An account set to push (Refresh 0) has an IMAP IDLE connection open, and its server announces new mail in the inbox
  kind: condition
  unattended: true
  entities:
  - entity: account
    effect: reads
    facts:
    - Refresh
  contexts:
    tui:
      place: tidemail::unified-inbox
- text: TideMail syncs that inbox and stores the new messages
  kind: product
  entities:
  - entity: message
    effect: creates
    facts:
    - From
    - To
    - Cc
    - Reply-To
    - Subject
    - Date
    - Body
    - Attachments
    - Authentication results
    - Read
    - Starred
    - Folder
  contexts:
    tui:
      place: tidemail::unified-inbox
- text: TideMail runs the enabled filter rules on the new messages
  kind: product
  entities:
  - entity: message
    effect: changes
    facts:
    - Read
    - Folder
  - entity: filter-rule
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::unified-inbox
- text: TideMail updates the inbox's unread count and, with desktop notifications on, announces the new mail
  kind: product
  entities:
  - entity: folder
    effect: changes
    facts:
    - Unread count
    - Last synced
  - entity: settings
    effect: reads
    facts:
    - Desktop notifications
  contexts:
    tui:
      place: tidemail::unified-inbox
---

# Receive mail the server pushes

## Trigger

New mail reaches an account that refreshes by push.

## Outcome

The mail is in the inbox as the server announces it, already filtered.

## Edge cases

- A push account also polls every 30 minutes, because a connection that hangs without dropping announces nothing.
- One notification names a single sender and subject; several are counted, with up to five listed.
