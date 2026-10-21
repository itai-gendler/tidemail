---
{}
---

# Compose

Writing and sending a message: the compose window, its attachments, templates and checks, and the command line's drafts and sends.

## Boundary

Owns drafts, templates and handing a finished message to the Outbox. It does not own delivery, retries or cancelling a queued message, which belong to the Outbox.
