---
domain: compose
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/templates.go#createTemplate
- kind: code
  role: implementation
  target: internal/ui/templates.go#cleanTemplateName
---

# Save template

Save the message being written as a new template (`n` in the template picker). Quoted text in a reply or forward is left out.
