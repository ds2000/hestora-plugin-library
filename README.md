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

- Gmail `0.1.0`
- LM Studio `0.2.0`
- Ollama local models `0.5.0`
- Zoho Mail `0.1.0`

The mailbox packages expose the native mailbox broker and unified setup wizard. The local-model
packages expose Hestora's bounded same-Mac and trusted-LAN/VPN runtime broker. Packages contain no
OAuth client secret, provider credential, refresh token, mailbox content or model weights.

## Publication

The packages and feed are generated from reviewed source in the main Hestora repository. Private signing
keys remain outside both repositories. Development feeds expire within seven days and are regenerated
before testing.

This is an internal development library, not a public community marketplace.
