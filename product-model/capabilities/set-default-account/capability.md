---
domain: accounts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#setSelectedDefault
- kind: code
  role: implementation
  target: internal/config/config.go#SetDefaultAccount
---

# Set default account

Mark the account new messages are sent from (`Space` in Accounts, shown as ★ [default]). It is also the account focused at startup.
