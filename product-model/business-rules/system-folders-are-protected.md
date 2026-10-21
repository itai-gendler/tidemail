---
appliesTo:
- type: capability
  id: rename-folder
- type: capability
  id: delete-folder
- type: capability
  id: move-folder
- type: capability
  id: hide-folder
references:
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#protectedFolderReason
---

# The Inbox and system folders keep their names and places

The Inbox, Sent, Drafts, Trash, Junk, Archive, All Mail, Starred, Important and Gmail's own folders cannot be renamed, deleted or moved in or out of a parent; they can be reordered. A folder holding one cannot be deleted, and the Inbox cannot be hidden.
