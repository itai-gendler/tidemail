---
scope: The TideMail terminal client, its mail commands and agent mode, and the storage, IMAP, SMTP, sign-in, filter and AI code behind them.
method: Static reading of the tracked Go source, docs and tests at the pinned commit; nothing was built or run.
covered:
- description: 'Three-pane client: panes, mail views, compose, Outbox, account, contact and filter managers, Settings and message rendering.'
  paths:
  - internal/ui/
  - main.go
  - shutdown_indicator.go
- description: 'Local cache: accounts, folders, messages, drafts, outbox, contacts, rules, snoozes and waits.'
  paths:
  - internal/db/
- description: IMAP sync, push and folder operations, and SMTP delivery.
  paths:
  - internal/imap/
  - internal/smtp/
- description: Server lookup, OAuth sign-in, configuration and keychain storage.
  paths:
  - internal/autodiscover/
  - internal/auth/
  - internal/config/
- description: Filter rules and AI providers.
  paths:
  - internal/filter/
  - internal/ai/
- description: Mail commands, compose wizard, agent checks, shared sending and templates.
  paths:
  - internal/cli/
  - internal/cliform/
  - internal/mailapp/
  - internal/mailtemplate/
- description: Conversation threading, attention signals, links, clipboard and image handling.
  paths:
  - internal/conversation/
  - internal/attention/
  - internal/browser/
  - internal/clipboard/
  - internal/richmail/
  - internal/termimage/
  - internal/omarchy/
exclusions:
- description: Go API for the separate Android app's bridge.
  paths:
  - mailcore/
- description: Manual test harnesses and preview commands.
  paths:
  - cmd/
- description: Release, packaging, installer and CI scripts.
  paths:
  - packaging/
  - scripts/
  - install.sh
  - deploy.sh
  - deploy.conf
  - harness.yaml
  - .github/
  - ansi_wave.go
- description: Example plugins for plugin authors.
  paths:
  - examples/
- description: Design sketches.
  paths:
  - sketches/
unmapped:
- description: 'Experimental plugins: running, reports, catalog install, settings, annotations, tag corrections and PGP through a plugin.'
  paths:
  - internal/plugin/
  - internal/plugincatalog/
  - internal/pluginquery/
  - internal/pgpmail/
  - internal/ui/plugins.go
  - internal/ui/plugin_annotations.go
  - internal/ui/plugin_bulk.go
  - internal/ui/plugin_card.go
  - internal/ui/plugin_catalog.go
  - internal/ui/plugin_cleanup.go
  - internal/ui/plugin_events.go
  - internal/ui/plugin_export.go
  - internal/ui/plugin_report.go
  - internal/ui/plugin_settings.go
  - internal/ui/plugin_view.go
  - internal/ui/settings_plugins.go
  - internal/ui/classification.go
  - internal/ui/pgp.go
  - internal/ui/pgp_compose.go
  - internal/cli/plugin.go
- description: In-app update checks and installs.
  paths:
  - internal/update/
  - internal/ui/update_ui.go
  - internal/ui/update_state.go
- description: Searchable help, the command palette, mouse context menus and the man page.
  paths:
  - internal/ui/help.go
  - internal/ui/commands.go
  - internal/ui/context_menu.go
  - man/
- description: About, Support and Changelog pages in Settings.
  paths:
  - internal/ui/settings_about_ocean.go
  - internal/ui/settings_support_cafe.go
  - internal/ui/support.go
  - internal/ui/settings_changelog.go
- description: Links, find in message, visual selection and copying from the reading pane.
  paths:
  - internal/ui/links.go
  - internal/ui/article_text.go
- description: Tag colors and the color picker.
  paths:
  - internal/ui/tag_colors.go
  - internal/ui/color_picker.go
- description: Native password dialog on the account form.
  paths:
  - internal/passprompt/
limitations: []
---

# Coverage
