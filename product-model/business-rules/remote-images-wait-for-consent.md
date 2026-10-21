---
appliesTo:
- type: capability
  id: load-remote-images
- type: capability
  id: read-message
references:
- kind: code
  role: implementation
  target: internal/richmail/remote.go
- kind: doc
  role: intent
  target: README.md
---

# Remote images load only when the person asks, one message at a time

Images embedded in a message show where the terminal can draw them, but images the message links to on the web stay blocked until the person presses `i` on that message.
