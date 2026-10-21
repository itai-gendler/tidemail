---
domain: accounts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#startOAuthSignIn
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#submitOAuthCode
- kind: code
  role: implementation
  target: internal/auth/oauth.go
- kind: doc
  role: intent
  target: docs/guide.md
---

# Sign in with OAuth

Sign an Outlook account (Outlook.com, Hotmail and Microsoft 365 / Exchange Online) in with Microsoft instead of a password: with the Auth row on OAuth, Ctrl+O starts the sign-in. TideMail uses Thunderbird's shared public client, which needs no setup, or the person's own Azure app when one is configured. Gmail sign-in with OAuth is unavailable while Google's approval is pending.
