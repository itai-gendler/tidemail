---
domain: settings
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/settings.go
- kind: code
  role: implementation
  target: internal/ai/ai.go#New
- kind: code
  role: implementation
  target: internal/ai/validate.go
---

# Change AI settings

Choose the AI provider (OpenAI, Claude, Gemini or a local Ollama server), its model and key in Settings → AI. AI summaries, grammar checks and filter creation stay off until a provider is configured; the key is kept in the system keychain.
