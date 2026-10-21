---
domain: accounts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#moveSelected
- kind: code
  role: implementation
  target: internal/config/config.go#ReorderAccounts
---

# Reorder accounts

Move an account up or down the list (Shift+K / Shift+J in Accounts). The order is the one used in the sidebar, the account list and the sender picker.
