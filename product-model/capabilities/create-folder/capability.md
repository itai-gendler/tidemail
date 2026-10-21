---
domain: folders
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#startNewFolder
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#createFolderOnServerCmd
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#validateFolderName
---

# Create folder

Create a real folder on the server from the left pane (`n`): on a folder it makes a subfolder, on an account or section header a top-level folder. Creating one is also offered in the move picker.
