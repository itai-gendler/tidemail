---
domain: accounts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#populateFormFrom
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#saveAccountCmd
---

# Edit account

Change an account's details in the account form (`e` in Accounts). Saving connects to the server again before the change is kept.
