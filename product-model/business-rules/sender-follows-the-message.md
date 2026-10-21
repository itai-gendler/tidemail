---
appliesTo:
- type: capability
  id: compose-message
- type: capability
  id: reply-to-message
- type: capability
  id: reply-to-all
- type: capability
  id: forward-message
references:
- kind: code
  role: implementation
  target: internal/config/config.go#DefaultAccount
- kind: code
  role: implementation
  target: internal/ui/compose.go#newReplyBase
---

# New mail starts from the default account; replies and forwards from the account the message arrived on

Compose starts from the account marked ★ [default], or the first account without one. Replies, reply-alls and forwards ignore the default and use the account that received the original. Whatever account is chosen brings its SMTP server, From address and signature.
