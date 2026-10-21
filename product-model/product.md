---
id: tidemail
summary: A keyboard-first terminal email client for IMAP and SMTP accounts, with a unified inbox, a durable outbox, local filter rules, contacts, optional AI tools and a command line for scripts and AI agents.
category: email-client
tags:
- email
- terminal
- tui
- imap
- smtp
- cli
authors:
- name: allisonhere
  url: https://github.com/allisonhere
license: MIT
languages:
- en
limitations:
- TideMail reads and sends mail only through IMAP and SMTP accounts, signing in with a password or with OAuth; servers that accept only NTLM or Kerberos sign-in are out of reach.
- 'Mail state belongs to the server: read state, stars, archive, move and delete go to the account''s IMAP server, and TideMail keeps a local cache only for speed and search.'
- Search, Needs You, Waiting on Them and the command line work only from mail TideMail has already cached; the command line never synchronizes mail.
- Hidden folders, folder order, snoozes, Needs You dismissals and stopped waits stay on this computer and never change mail on the server.
- AI summaries, grammar checks and filter creation use an outside provider the person configures; AI stays off until one is configured.
references:
- kind: doc
  role: intent
  target: README.md
- kind: doc
  role: intent
  target: docs/guide.md
- kind: doc
  role: intent
  target: docs/cli.md
- kind: doc
  role: context
  target: docs/architecture.md
- kind: doc
  role: context
  target: STATUS.md
- kind: doc
  role: context
  target: AGENTS.md
- kind: code
  role: implementation
  target: main.go#main
---

# TideMail

TideMail is an email client for the terminal. One three-pane screen holds the accounts and folders, the message list and the reading pane, and every action has a key. It connects to any IMAP and SMTP account (Gmail, Outlook, Yahoo and iCloud are built in), keeps a local cache for speed and search, and leaves the mail state on the server. Outgoing mail goes through a durable outbox with an undo window, filter rules run locally on arriving mail, and **Needs You**, **Waiting on Them** and **Snoozed** gather what still needs attention across accounts. The `tidemail` command line shares the same accounts, cache and outbox, so scripts and AI agents can read, draft and send within the capabilities the person grants.

## Intent

"Mail for people who live in a terminal." TideMail "keeps your accounts, message list, and reading pane on one screen. It speaks IMAP and SMTP, stores its cache on your machine, and gives the keyboard the good seat." Its highlights put it plainly: "NO config file editing, all in the GUI", "One view for every account", "A few seconds to change your mind" and "An outbox you can trust".
