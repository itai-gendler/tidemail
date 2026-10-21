---
appliesTo:
- type: capability
  id: create-folder
- type: capability
  id: rename-folder
- type: capability
  id: delete-folder
- type: capability
  id: move-folder
references:
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go
---

# One folder change runs on the server at a time

While a create, rename, move or delete is still running, another is refused with a short notice, so a quick second keypress cannot act on a name that is changing.
