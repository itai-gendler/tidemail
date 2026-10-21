---
singleton: true
domain: settings
references:
- kind: code
  role: implementation
  target: internal/config/config.go#DefaultConfig
- kind: code
  role: implementation
  target: internal/ui/settings.go
---

# Settings

TideMail's own preferences, kept once in its configuration file and edited in Settings.

## Information kept

- **Theme** — the color theme; every built-in theme meets contrast minimums
- **Default account** — the account new messages start from and the one focused at startup; without one, the first account
- **Mark read on open** — mark a message read when it is opened; on by default
- **Mark read on focus** — mark a message read when the cursor rests on it
- **Threaded conversations** — group the message list into conversations
- **Starred first** — list starred messages first
- **Images** — Auto shows embedded images inline where the terminal can draw them; Off uses text placeholders everywhere
- **Desktop notifications** — notify about new mail; on by default
- **Mouse support** — click, double-click, wheel and right-click menus; off by default
- **Confirm quit** — ask before quitting; on by default
- **Compose keys** — the standard editor or Vim keys
- **Spell check** — underline misspelled words while composing; off by default
- **Spell check language** — English (US and GB spellings) or Español
- **Send delay** — seconds an outgoing message waits before it leaves, 5 by default; 0 sends at once
- **Maximum attempts** — total delivery attempts including the first, 3 by default; 1 turns automatic retries off
- **AI provider** — none, OpenAI, Claude, Gemini or Ollama
- **AI model** — the model used with that provider
- **AI key** — the provider's API key, kept in the system keychain
- **Mark read after summary** — mark a message read once it has been summarized
- **Summary save folder** — where a summary is saved as a Markdown file
- **Quit after send or draft** — `tidemail cli` exits after a send or draft instead of returning to its menu
- **Skip review step** — the CLI wizard goes from attachments straight to saving or to the undo countdown
- **Include signature by default** — the CLI wizard preselects the account signature; on by default
