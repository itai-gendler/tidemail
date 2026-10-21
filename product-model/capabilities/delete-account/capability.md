---
domain: accounts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#updateConfirmDelete
- kind: code
  role: implementation
  target: internal/ui/model.go#deleteAccountDatabaseCmd
---

# Delete account

Remove an account from TideMail (`d` in Accounts, then confirm). Its configuration and its cached folders and mail go; the mail on the server is untouched.
