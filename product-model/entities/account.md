---
domain: accounts
relations:
- entity: folder
  verb: has
  cardinality: one-to-many
- entity: draft
  verb: holds
  cardinality: one-to-many
- entity: outgoing-message
  verb: sends
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: internal/config/config.go#AccountConfig
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#validateAccountForConnect
- kind: doc
  role: intent
  target: docs/guide.md
---

# Account

One mail account: an IMAP server to read from and an SMTP server to send through, with the identity mail is sent as. Its generated id links it to its cached mail, drafts, queued mail and keychain credentials, so renaming it never cross-wires anything.

## Information kept

- **Name** — the display name shown in the sidebar, the account list and the sender picker; two accounts may share one
- **Provider** — Gmail, Outlook, Yahoo, iCloud or Custom; the four named providers bring their servers built in
- **Email / login** — the login the server issues: a full address for the named providers, anything the host issues for Custom
- **Password** — the password or app password, kept in the system keychain
- **Auth** — App password or OAuth; it becomes OAuth only after a completed sign-in, and the refresh token is kept in the keychain
- **IMAP server** — host, port and TLS for reading mail
- **SMTP server** — host, port and TLS for sending mail
- **From address** — the address mail is sent as, optionally with a name; blank sends as the login when the login is an address
- **Signature** — multi-line text added to outgoing mail
- **Color** — accents the account's own folders and tints its messages in the combined views
- **Refresh** — 0 for push through IMAP IDLE with a 30-minute safety poll (the default), a number of minutes to poll, or -1 for manual only
- **Position** — where the account appears in the sidebar, the account list and the sender picker
