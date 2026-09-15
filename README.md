# Hestora plugin library

This repository is the first-party distribution origin for optional Hestora plugins. The desktop app
ships without these packages and reads the short-lived signed feed for its platform when the user opens
the plugin library.

## Layout

- `index/v1/<channel>/<platform>.feed.json` — bounded signed catalogue feed.
- `entries/<plugin-id>/<version>.signed-entry.json` — independently signed listing and permission
  evidence.
- `packages/<plugin-id>/<version>/*.hestora-plugin` — deterministic signed packages.
- `packages/<plugin-id>/<version>/*.release.json` — reproducible build receipts.
- `trust/v1/*.json` — public development trust metadata; never private keys.

The app pins the accepted catalogue and package public keys. A repository change cannot grant new
permissions, change a package or redirect a download without producing new valid signatures.

## Current development packages

- Claude Code adapter `1.1.0`
- Codex CLI adapter `1.1.0`
- Constellation `0.1.0`
- Gmail `0.1.0`
- Grafana OTLP `0.1.0`
- Jira Cloud `1.2.0`
- LM Studio `0.2.0`
- Ollama local models `0.5.0`
- Zoho Mail `0.1.0`

The mailbox packages expose the native mailbox broker and unified setup wizard. The local-model
packages expose Hestora's bounded same-Mac and trusted-LAN/VPN runtime broker. Packages contain no
OAuth client secret, provider credential, refresh token, mailbox content or model weights.

The Codex package supplies isolated admission checks and enables Hestora's native provider broker.
Installation requires a project grant, successful isolation and behaviour checks, and explicit
enablement. An existing Codex CLI login does not bypass these steps.

Claude Code `1.1.0` supports Hestora `0.8.0-beta.5.105.1` and later. Refresh the library, install,
check isolation and behaviour, then enable it for selected projects. It uses the existing native
Claude broker and provider-owned sign-in, not a redistributed CLI or copied subscription token.
On older betas, configure sign-in and project grants under **Settings → CLI accounts**. The newer
guided Configure dialog and official provider icon require the next host UI build; a library
refresh alone cannot replace application screens. A login check is not a live inference test.

Jira Cloud requires Hestora `0.8.0-beta.5.104` or newer with the September 7 Jira pilot update.
It supports separate connections for multiple accounts/sites and verifies identity, project and JQL
before saving. Sync is a separate read-only action. Scoped API tokens use the Atlassian API gateway;
legacy unscoped tokens are available under Advanced. Jira Cloud `1.2.0` adds publication of an
exact, reviewed support-update draft through the host broker. Updating requires review of the new
`jira:comments` write permission; it never grants missing Jira-side account or API-token permissions.
Intake remains read-only, and installation never posts a comment. Use Hestora beta `5.109.4` for
the accompanying draft, connection-recovery, retained-formatting and closed-ticket sync fixes.
Browser OAuth is not included. Start with a narrowly scoped filter and a few known tickets.

### Constellation

Use Hestora beta `5.109.4` for the current project and workspace Observatory. In **Settings →
Extensions**, refresh the library, review Constellation, install it and enable it for the projects
you choose. Open **Observatory** inside a project, or **Workspace observatory** from Mission Control.
**Separate window** creates a window you can move to another display.

Hover or keyboard-focus a star for a glance; click to pin it. Follow its relationships, open its
workflow and use **Back → Observatory** to return to the same selection and viewpoint. Retained
source-only reference tickets link to their source without creating a workflow. Large groups are
paged; search and List view provide an alternative to the map.

This is a signed, declarative visualisation: no executable plugin code, connector credentials,
network access or data export. It displays authorised, retained project records; it does not sync
remote boards, start investigations or spend AI tokens. Other source plugins own intake scopes.
Workspace projects remain separate. Constellation is the first released view; Atlas and Signal
Loom remain concepts.

Display care includes gentle drift, motion pause, idle dimming and blanking. Reduce Motion is
honoured. Keep the display's own protection enabled; movement cannot guarantee against burn-in.

## Publication

The packages and feed are generated from reviewed source in the main Hestora repository. Private signing
keys remain outside both repositories. Development feeds expire within seven days and are regenerated
before testing.

This is an internal development library, not a public community marketplace.
