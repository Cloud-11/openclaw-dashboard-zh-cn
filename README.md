<p align="center">
  <img src="./icon.png" alt="OpenClaw Dashboard Plus icon" width="160">
</p>

# OpenClaw Dashboard Plus

Browser-extension-first tooling for OpenClaw Dashboard, with an optional Chinese translation userscript.

English is the canonical README for this repository.

[English](./README.md) | [简体中文](./docs/readme/README.zh-CN.md) | [繁體中文](./docs/readme/README.zh-TW.md) | [日本語](./docs/readme/README.ja.md) | [한국어](./docs/readme/README.ko.md) | [Français](./docs/readme/README.fr.md) | [Español](./docs/readme/README.es.md) | [Русский](./docs/readme/README.ru.md) | [Deutsch](./docs/readme/README.de.md) | [Tiếng Việt](./docs/readme/README.vi.md) | [Filipino](./docs/readme/README.fil.md) | [العربية](./docs/readme/README.ar.md)

## Overview

OpenClaw Dashboard Plus ships in two forms:

- A browser extension built into `dist/extension/`
- `openclaw-dashboard-plus-zh.user.js` as an optional Chinese translation userscript for Tampermonkey, ScriptCat, and similar managers

The browser extension is the primary delivery format. The userscript is kept as a lighter Chinese translation entry for environments where installing the extension is not convenient.

## Features

- Separate content language and popup UI language settings
- Remote metadata and locale updates from GitHub and Gitee
- Browser extension popup with runtime settings, cache controls, and version info
- Theme controls for preset, font, font size, and independent UI repair toggles
- Remote style-module delivery for HTML, CSS, and JSON assets without shipping remote JavaScript
- Shared project icon across documentation and browser extension assets
- Build output that is kept under `dist/` instead of mixing generated files with source files

## Usage

1. Build the extension with `node build-extension.mjs`, or download the packaged zip artifact from GitHub Actions.
2. Load `dist/extension/` in `chrome://extensions` or `edge://extensions` with Developer mode enabled.
3. Open your local OpenClaw panel, such as `http://127.0.0.1:18789`.
4. In the extension popup, use:
   - `Settings` to enable translation and define the allowed hosts and ports.
   - `Features` to select the OpenClaw UI preset, font, font size, and toggle style override, style repair, select-style fix, or code-block styling independently.
   - `Languages` to switch the OpenClaw content language, download remote locale packs, and clear cached bundles.
   - `About` to refresh remote metadata and check current extension/OpenClaw compatibility info.
5. Save runtime or theme settings after making changes. Remote theme/style assets are cached locally after download and reused until cleared.

## Build

Prerequisites:

- Node.js 22 is the reference runtime used by the GitHub Actions workflow.
- PowerShell is required for `package-extension-zip.mjs`.
- Chrome or Edge is required for `package-crx.mjs`.

Commands:

1. Build the unpacked browser extension:
   `node build-extension.mjs`
2. Package a zip archive for browser extension distribution:
   `node package-extension-zip.mjs`
3. Optional: package a local CRX file:
   `node package-crx.mjs`

Outputs:

- `dist/extension/`: generated unpacked browser extension
- `dist/openclaw-dashboard-plus-extension.zip`: packaged extension zip
- `dist/openclaw-dashboard-plus.crx`: optional local CRX build

## Feature And File Guide

- `extension-src/`: extension source, popup UI, icons, and browser content patches
- `extension-src/style-bundle.json`: manifest for remote-loadable style modules
- `extension-src/style-modules/`: modular style payloads delivered as CSS, HTML, or JSON
- `language-packs/`: built or synced OpenClaw content locale bundles
- `ui-locales/`: popup UI locale strings
- `theme-presets.json`: built-in OpenClaw theme preset definitions
- `plugin-metadata.json`: repository metadata, compatibility, and remote source definitions
- `build-extension.mjs`: generates `dist/extension/` and syncs packaged assets
- `package-extension-zip.mjs`: creates the extension zip artifact in `dist/`
- `package-crx.mjs`: optional local CRX packaging helper
- `dist/extension/`: generated output that should be treated as build artifacts
- `openclaw-dashboard-plus-zh.user.js`: optional Chinese translation userscript retained for userscript-based installs

## Install

### Userscript

1. Open `openclaw-dashboard-plus-zh.user.js`
2. Install it with Tampermonkey, ScriptCat, or another compatible userscript manager

### Browser Extension ZIP

1. Download `openclaw-dashboard-plus-extension.zip` from GitHub Actions artifacts or releases
2. Extract it to a stable folder
3. Open `chrome://extensions` or `edge://extensions`
4. Enable Developer mode
5. Click `Load unpacked`
6. Select the extracted folder

### Local Unpacked Extension

1. Run `node build-extension.mjs`
2. Open `chrome://extensions` or `edge://extensions`
3. Enable Developer mode
4. Click `Load unpacked`
5. Select `dist/extension/`

## GitHub Actions

The repository includes a Windows-based GitHub Actions workflow that:

- Builds `dist/extension/`
- Packages `dist/openclaw-dashboard-plus-extension.zip`
- Uploads both the zip archive and unpacked extension as workflow artifacts

## Pull Requests

- Make source changes in `extension-src/`, locale sources, metadata files, or build scripts. Do not manually edit `dist/extension/`.
- Keep the browser extension as the primary delivery target. Only change `openclaw-dashboard-plus-zh.user.js` when the userscript itself truly needs maintenance.
- Remote-delivered theme assets should stay limited to HTML, CSS, and JSON payloads. Do not introduce remote JavaScript execution paths.
- Include reproduction steps for fixes, and attach screenshots or short notes when changing popup UI or OpenClaw styling behavior.
- Run the relevant build command before opening a PR, and mention the verification result in the PR description.
- Update the English README first for user-facing changes. Sync localized docs when the behavior or workflow meaningfully changes.

## Screenshots

![Extension popup preview](./image.png)
![Extension install preview](./image2.png)

## License

This project is released under the [MIT License](./LICENSE).
