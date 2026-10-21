---
domain: compose
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/templates.go#insertTemplate
- kind: code
  role: implementation
  target: internal/mailtemplate/mailtemplate.go#Fill
- kind: doc
  role: intent
  target: docs/guide.md
---

# Insert template

Insert a canned reply at the cursor (F6 in compose, or Insert template… in the command palette). The highlighted template is previewed; inserting fills {first_name}, {name}, {my_name} and {date} and sets the subject only if it is empty.
