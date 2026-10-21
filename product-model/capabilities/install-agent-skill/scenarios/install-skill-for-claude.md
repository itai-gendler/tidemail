---
kind: primary
routes:
  cli: Command line
steps:
- text: The person runs `tidemail install-skill claude`
  kind: actor
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
- text: TideMail writes its SKILL.md to ~/.claude/skills/tidemail/ and says to reload the agent
  kind: product
  actor: user
  entities: []
  contexts:
    cli:
      place: command-line
---

# Install the skill for Claude Code

## Trigger

The person wants their agent to handle mail through TideMail.

## Outcome

After a reload, the agent knows the commands, the capabilities and that every send needs the person's approval.

## Edge cases

- Codex and Pi share ~/.agents/skills/tidemail/; Hermes uses HERMES_HOME when set.
- --dry-run prints the destination and writes nothing; `tidemail skill` prints the skill itself.
