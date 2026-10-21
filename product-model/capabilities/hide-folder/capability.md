---
domain: folders
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#toggleHideSelectedFolder
- kind: code
  role: implementation
  target: internal/db/mailbox_prefs.go#SetMailboxHidden
---

# Hide folder

Hide a folder and its subfolders from TideMail's sidebar (`H`). Nothing changes on the server, and the Inbox can't be hidden.
