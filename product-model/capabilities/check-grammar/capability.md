---
domain: compose
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/model.go#handleCompose
- kind: code
  role: implementation
  target: internal/ai/polish.go
---

# Check grammar

Have the configured AI provider proofread what the person wrote (Ctrl+G in compose). Only the person's own text is checked, never the quoted original; the corrected text is previewed, and `y` accepts it while `n` or Esc keeps the original.
