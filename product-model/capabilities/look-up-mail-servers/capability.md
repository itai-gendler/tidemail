---
domain: accounts
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/autodiscover/autodiscover.go
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#startDiscovery
- kind: code
  role: implementation
  target: internal/ui/account_manager.go#applyDiscovery
- kind: doc
  role: intent
  target: docs/guide.md
---

# Look up mail servers

Fill in a Custom account's servers from its email domain: DNS SRV records first (IMAP over TLS only), then the domain's MX records for Google, Microsoft 365, iCloud and Yahoo, then the domain's own autoconfig file over HTTPS. It runs when the person moves past the email row with both host rows empty, or on Ctrl+L, and only fills in the form: nothing connects or saves.
