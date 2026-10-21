---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/compose.go#NewReply
- kind: code
  role: implementation
  target: internal/ui/compose.go#quotableText
---

# Reply

Answer the sender of the message in the list or the reading pane (`r`). The reply goes to the Reply-To address when the sender gave one, quotes the readable text of the original and is sent from the account the message arrived on.
