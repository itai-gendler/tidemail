---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail templates list --json`
  kind: actor
  actor: user
  entities:
  - entity: template
    effect: reads
    facts: []
  contexts:
    cli:
      place: command-line
- text: TideMail returns each template's name and subject
  kind: product
  actor: user
  entities:
  - entity: template
    effect: reads
    facts:
    - Name
    - Subject
  contexts:
    cli:
      place: command-line
---

# List the templates

## Trigger

A script needs to know which canned replies exist.

## Outcome

The script has the template names to pass to --template.
