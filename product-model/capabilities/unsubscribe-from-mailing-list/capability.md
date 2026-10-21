---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/unsubscribe.go#handleUnsubscribe
- kind: code
  role: implementation
  target: internal/ui/unsubscribe.go#performUnsubscribe
- kind: code
  role: implementation
  target: internal/ui/unsubscribe.go#oneClickUnsubscribeCmd
---

# Unsubscribe

Leave a mailing list from the message being read (Ctrl+U). TideMail uses the sender's List-Unsubscribe header, preferring a web link to an email address, and otherwise a link labelled unsubscribe in the message. A web unsubscribe always asks first and shows where it goes.
