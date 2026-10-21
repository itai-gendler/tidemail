---
kind: validation
routes:
  tui: TideMail
steps:
- text: The person fills in a Custom account whose login is not an address, such as DOMAIN\alice, and leaves From address blank
  kind: actor
  actor: user
  entities:
  - entity: account
    effect: reads
    facts: []
  contexts:
    tui:
      place: tidemail::account-form
- text: The person presses Ctrl+S to save
  kind: actor
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: The login is not an address and From address is empty
  kind: condition
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
- text: TideMail marks the From address row red, puts the cursor on it and says an address is required; nothing connects or saves
  kind: product
  actor: user
  entities: []
  contexts:
    tui:
      place: tidemail::account-form
---

# Refuse a login that leaves nothing to send as

## Trigger

A host issues a login that is not an email address.

## Outcome

The form stays open with From address marked; once it holds an address, saving goes ahead.

## Edge cases

- A From address that is a name with no address is refused the same way.
- `#` typed where `@` belongs (info#example.com) is refused in any address field.
- Hosts must be host names, not URLs or host:port; ports must be 1–65535.
- The four named providers require a full address in the Email row.
