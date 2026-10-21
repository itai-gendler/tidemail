---
availability:
- place: tidemail
- place: command-line
- place: agent-skill
references:
- kind: code
  role: implementation
  target: internal/ui/sync.go#loadMailboxMessagesCmd
- kind: code
  role: implementation
  target: internal/ui/sync.go#loadOlderMessagesCmd
- kind: code
  role: implementation
  target: internal/ui/needs_you.go#loadNeedsYouCmd
- kind: code
  role: implementation
  target: internal/ui/waiting.go#loadWaitingCmd
- kind: code
  role: implementation
  target: internal/cli/mail_reads.go#RunMailRead
- kind: doc
  role: intent
  target: docs/cli.md
---

# Browse messages

List the cached messages of a folder or of one of the combined views: the Unified Inbox, Needs You, Waiting on Them and Snoozed. `u` narrows the list to unread mail, `t` puts starred messages first and `g` groups conversations; moving past the last message fetches the next 100 from the server. From the command line, `tidemail messages list` pages through the cached Unified Inbox without connecting to the server.
