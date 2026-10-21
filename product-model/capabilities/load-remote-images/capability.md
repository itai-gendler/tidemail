---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/rich_images.go
- kind: code
  role: implementation
  target: internal/richmail/remote.go
- kind: doc
  role: intent
  target: README.md
---

# Load remote images

Load the remote images in the message being read (`i`). Remote images stay blocked for privacy until the person asks, one message at a time; images carried in the message itself show without asking where the terminal can draw them.
