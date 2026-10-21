---
appliesTo:
- type: entity
  id: account
  facts:
  - Auth
- type: capability
  id: sign-in-with-oauth
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#keepsPausedGoogleOAuth
- kind: doc
  role: context
  target: STATUS.md
---

# An account uses OAuth only after a completed sign-in

Auth becomes OAuth when the person finishes a sign-in; a token left in the keychain never switches an account on its own. Gmail, Yahoo and iCloud take an app password; Outlook mailboxes sign in with OAuth.
