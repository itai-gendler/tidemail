---
domain: accounts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#submitForm
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#saveAccountCmd
- kind: code
  role: implementation
  target: internal/ui/model.go#saveAccountDatabaseCmd
- kind: doc
  role: intent
  target: docs/guide.md
---

# Add account

Add a mail account from the account manager (`M`, then `a`). Gmail, Outlook, Yahoo and iCloud bring their servers built in; any other IMAP and SMTP server, including on-premises Exchange, is a **Custom** account. Saving checks the form, then connects to the IMAP server and lists its folders before anything is kept.
