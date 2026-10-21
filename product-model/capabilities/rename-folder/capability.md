---
domain: folders
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#startRenameFolder
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#renameFolderCmd
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#renameClash
---

# Rename folder

Rename a folder on the server (`r` in the left pane); its subfolders come along. The Inbox and system folders cannot be renamed.
