---
{}
---

# Outbox

Every outgoing message from queueing to delivery: inspecting, retrying, cancelling, clearing and processing the queue.

## Boundary

Owns outgoing messages once they are queued. It does not own writing them, which is Compose, nor the copy filed in the Sent folder after delivery, which is ordinary mail.
