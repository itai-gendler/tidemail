---
domain: folders
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#moveSelectedFolder
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#indentSelectedFolder
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#reparentFolder
---

# Move folder

Move a folder within its account's tree. Shift+K / Shift+J walk it up or down one row: passing a sibling reorders it (an order local to TideMail), moving onto an open folder with subfolders puts it inside, and moving past a parent's first or last subfolder takes it out. `>` nests it under the folder just above and `<` moves it out of its parent. Moving in or out is a real move on the server, subfolders included.
