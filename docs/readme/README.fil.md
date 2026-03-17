<p align="center">
  <img src="../../icon.png" alt="OpenClaw Dashboard Plus icon" width="160">
</p>

# OpenClaw Dashboard Plus

Browser extension tool para sa OpenClaw Dashboard.

> Paalala: hindi bihasa ang developer sa Filipino. Ginawa ang dokumentong ito gamit ang AI model at maaaring may hindi natural na pananalita.

[English](../../README.md) | [简体中文](./README.zh-CN.md) | [繁體中文](./README.zh-TW.md) | [日本語](./README.ja.md) | [한국어](./README.ko.md) | [Français](./README.fr.md) | [Español](./README.es.md) | [Русский](./README.ru.md) | [Deutsch](./README.de.md) | [Tiếng Việt](./README.vi.md) | [Filipino](./README.fil.md) | [العربية](./README.ar.md)

## Pangkalahatan

Ang OpenClaw Dashboard Plus ay browser extension na lamang at bino-build sa `dist/extension/`.

Nagdadala ito ng:

- Hiwalay na setting para sa wika ng nilalaman ng OpenClaw at wika ng popup UI
- Pagkuha ng metadata, language pack, at style asset mula sa GitHub o Gitee
- Theme controls para sa UI style, font, laki ng font, at visual repairs
- Iisang icon at metadata chain para sa dokumentasyon at extension

## Mga Tampok

- Popup tabs na `Settings`, `Features`, `Languages`, at `About`
- Remote refresh para sa metadata, language packs, theme presets, at style modules
- Theme assets na HTML / CSS / JSON lang, walang remote JavaScript
- Modular na layout gamit ang `extension-src/`, `language-packs/`, `ui-locales/`, at `plugin-metadata.json`
- Lahat ng build output ay nasa `dist/`

## Paggamit

1. Patakbuhin ang `node build-extension.mjs` o i-download ang ZIP artifact mula sa GitHub Actions.
2. Buksan ang `chrome://extensions` o `edge://extensions` at i-on ang Developer mode.
3. I-load ang `dist/extension/` bilang unpacked extension.
4. Buksan ang OpenClaw panel, halimbawa `http://127.0.0.1:18789`.
5. Gamitin ang mga tab sa popup:
   - `Settings`: paganahin ang translation at itakda ang pinapayagang host at port
   - `Features`: pumili ng UI preset, font, laki, at style repair toggles
   - `Languages`: palitan ang content language, i-refresh ang remote packs, at linisin ang cache
   - `About`: i-refresh ang remote metadata at tingnan ang compatibility info
6. I-save ang settings pagkatapos ng pagbabago. Mananatiling lokal ang cached remote assets hanggang burahin sa popup.

## Build

Mga kailangan:

- Node.js 22 ang reference runtime.
- Kailangan ng `package-extension-zip.mjs` ang PowerShell.
- Kailangan ng `package-crx.mjs` ang Chrome o Edge.

Mga utos:

1. I-build ang unpacked extension:
   `node build-extension.mjs`
2. Gumawa ng ZIP para sa distribution:
   `node package-extension-zip.mjs`
3. Opsyonal: gumawa ng lokal na CRX:
   `node package-crx.mjs`

Mga output:

- `dist/extension/`: generated unpacked extension
- `dist/openclaw-dashboard-plus-extension.zip`: distribution ZIP
- `dist/openclaw-dashboard-plus.crx`: opsyonal na lokal na CRX

## Gabay Sa Mga File

- `extension-src/`: source ng extension, popup UI, icons, theme presets, at content logic
- `extension-src/content-main.js`: source ng content script
- `extension-src/style-bundle.json`: manifest ng remote-loadable style modules
- `extension-src/style-modules/`: modular na CSS / HTML / JSON assets
- `extension-src/theme-presets.json`: built-in theme preset definitions
- `language-packs/`: OpenClaw content language packs
- `ui-locales/`: popup UI strings at localized preset labels
- `plugin-metadata.json`: canonical metadata para sa versions, remote sources, at available locales
- `build-extension.mjs`: bumubuo ng `dist/extension/`
- `package-extension-zip.mjs`: gumagawa ng ZIP sa `dist/`
- `package-crx.mjs`: helper para sa lokal na CRX

## Install

### Extension ZIP

1. I-download ang `openclaw-dashboard-plus-extension.zip` mula sa GitHub Actions artifacts o Releases.
2. I-extract ito sa stable na folder.
3. Buksan ang `chrome://extensions` o `edge://extensions`.
4. I-on ang Developer mode.
5. I-click ang `Load unpacked`.
6. Piliin ang extracted folder.

### Lokal Na Unpacked Extension

1. Patakbuhin ang `node build-extension.mjs`.
2. Buksan ang `chrome://extensions` o `edge://extensions`.
3. I-on ang Developer mode.
4. I-click ang `Load unpacked`.
5. Piliin ang `dist/extension/`.

## GitHub Actions

May Windows-based GitHub Actions workflow ang repository na awtomatikong:

- Nagbu-build ng `dist/extension/`
- Gumagawa ng `dist/openclaw-dashboard-plus-extension.zip`
- Nag-a-upload ng ZIP at unpacked extension bilang artifacts

## Pull Request

- Magbago sa `extension-src/`, locales, metadata, o build scripts. Huwag direktang i-edit ang `dist/extension/`.
- Extension-only na ang repository. Huwag ibalik ang lumang script packaging o parallel delivery path.
- Ang remote theme assets ay dapat manatiling HTML / CSS / JSON lang, walang remote JavaScript execution.
- Para sa UI o style fixes, magdagdag ng reproduction steps at screenshots kung makakatulong.
- Patakbuhin ang kaukulang build bago magbukas ng PR at ilagay ang verification result.

## Mga Larawan

![Extension popup preview](../../image.png)
![Extension install preview](../../image2.png)

## Lisensya

Ang proyektong ito ay nasa ilalim ng [MIT License](../../LICENSE).
