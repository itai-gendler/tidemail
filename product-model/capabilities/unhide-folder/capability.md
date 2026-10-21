---
domain: folders
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#toggleShowHiddenFolders
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#toggleHideSelectedFolder
---

# Unhide folder

Bring a hidden folder back into the sidebar: Show hidden folders in the command palette lists them marked (hidden), and `H` on one unhides it.
