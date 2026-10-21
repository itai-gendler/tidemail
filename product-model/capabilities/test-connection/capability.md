---
domain: accounts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#testForm
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#testAccountCmd
---

# Test connection

Check an account form's details against the server (Ctrl+T) without saving: TideMail validates the rows, connects to the IMAP server and lists its folders.
