---
kind: validation
routes:
  cli: Command line
steps:
- text: The person runs `tidemail install-skill codex` where a TideMail skill is already installed
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail leaves the existing skill alone and says to review it and use --force to replace it
  kind: product
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
---

# Refuse to replace an existing skill

## Trigger

A skill is already there.

## Outcome

Nothing is overwritten.
