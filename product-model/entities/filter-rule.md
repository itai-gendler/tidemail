---
domain: filters
references:
- kind: code
  role: implementation
  target: internal/filter/filter.go#Rule
- kind: code
  role: implementation
  target: internal/ui/filter_runner.go#firstMatch
---

# Filter rule

A local mail rule built once from a plain-English description and then matched against messages on this computer without an AI call per message.

## Information kept

- **Description** — the plain-English request it was built from, shown as its name
- **Account** — the one account it applies to, or all accounts
- **Conditions** — tests on From, To, Cc, Subject, body or attachments (contains, does not contain, equals, starts with, ends with), all of which or any of which must match
- **Action** — move to a folder, mark read, archive, delete, or send to spam
- **Target folder** — the folder a move action files into
- **Order** — its place in the list; rules are tried in this order

## States

### Enabled

It runs on arriving mail and in manual runs.

### Disabled

It is kept but never runs.
