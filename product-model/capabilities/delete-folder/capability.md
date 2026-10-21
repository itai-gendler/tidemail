---
domain: folders
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#startDeleteFolder
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#folderDeleteConfirmText
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#deleteFolderCmd
---

# Delete folder

Delete a folder from the server (`d` in the left pane, then confirm), with its subfolders and every message in them. The Inbox and system folders cannot be deleted.
