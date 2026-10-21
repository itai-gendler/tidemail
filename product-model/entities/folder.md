---
domain: folders
relations:
- entity: message
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: internal/db/accounts.go#FindArchiveMailbox
- kind: code
  role: implementation
  target: internal/ui/folder_manage.go#protectedFolderReason
---

# Folder

A real folder (or Gmail label) on an account's server, shown as a tree in the left pane. TideMail recognizes the Inbox and the Sent, Drafts, Trash, Junk and Archive folders by their server flags or common names.

## Information kept

- **Name** — the folder's name on the server; a folder like Work/Projects sits under Work
- **Parent** — the folder it is nested in, when the server has a folder hierarchy
- **Kind** — Inbox, Sent, Drafts, Trash, Junk, Archive, another system folder, or the person's own
- **Unread count** — unread messages in it; a collapsed folder's count includes its subfolders
- **Last synced** — when its messages were last fetched from the server
- **Hidden** — whether TideMail leaves it out of the sidebar; local to TideMail
- **Order** — its place among its siblings in TideMail's sidebar; local to TideMail
