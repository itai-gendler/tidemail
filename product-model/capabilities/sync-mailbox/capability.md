---
availability:
- place: tidemail
references:
- kind: code
  role: implementation
  target: internal/ui/sync.go#syncMailboxCmdWithMode
- kind: code
  role: implementation
  target: internal/ui/sync.go#syncPollInterval
- kind: code
  role: implementation
  target: internal/ui/sync.go#shouldAutoSyncFolder
- kind: code
  role: implementation
  target: internal/ui/sync_all.go#requestSyncAll
- kind: code
  role: implementation
  target: internal/ui/idle.go
- kind: code
  role: implementation
  target: internal/imap/idle.go
- kind: doc
  role: intent
  target: docs/guide.md
---

# Sync mailbox

Fetch a folder's new mail from the server and reconcile the cache with it: messages removed elsewhere go, read state and stars set in another client come back, and saved filter rules run on what arrived. `s` syncs the selected folder (every account's inbox from the Unified Inbox), Enter on a folder fetches it at once, `F` syncs every folder. On their own, accounts refresh their inboxes by push or polling, and a non-inbox folder refreshes quietly when the person rests on it and its cache is more than 15 minutes old.
