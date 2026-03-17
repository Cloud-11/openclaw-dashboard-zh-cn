<p align="center">
  <img src="../../icon.png" alt="OpenClaw Dashboard Plus icon" width="160">
</p>

# OpenClaw Dashboard Plus

Инструмент расширения браузера для OpenClaw Dashboard.

> Примечание: разработчик не владеет русским языком. Этот документ создан с помощью модели ИИ и может содержать неестественные формулировки.

[English](../../README.md) | [简体中文](./README.zh-CN.md) | [繁體中文](./README.zh-TW.md) | [日本語](./README.ja.md) | [한국어](./README.ko.md) | [Français](./README.fr.md) | [Español](./README.es.md) | [Русский](./README.ru.md) | [Deutsch](./README.de.md) | [Tiếng Việt](./README.vi.md) | [Filipino](./README.fil.md) | [العربية](./README.ar.md)

## Обзор

OpenClaw Dashboard Plus теперь поставляется только как расширение браузера, собираемое в `dist/extension/`.

Проект добавляет:

- Раздельные настройки языка контента OpenClaw и языка интерфейса popup
- Загрузку метаданных, языковых пакетов и стилевых ресурсов из GitHub или Gitee
- Настройки темы для UI-стиля, шрифта, размера шрифта и визуальных исправлений
- Общую цепочку иконок и метаданных для документации и расширения

## Возможности

- Вкладки popup `Settings`, `Features`, `Languages` и `About`
- Удаленное обновление метаданных, языковых пакетов, пресетов темы и стилевых модулей
- Доставка тем только как HTML / CSS / JSON без удаленного JavaScript
- Модульная структура с `extension-src/`, `language-packs/`, `ui-locales/` и `plugin-metadata.json`
- Все сборочные артефакты находятся в `dist/`

## Использование

1. Запустите `node build-extension.mjs` или скачайте ZIP из GitHub Actions.
2. Откройте `chrome://extensions` или `edge://extensions` и включите режим разработчика.
3. Загрузите `dist/extension/` как распакованное расширение.
4. Откройте панель OpenClaw, например `http://127.0.0.1:18789`.
5. Используйте вкладки popup:
   - `Settings`: включить перевод и задать разрешенные хосты и порты
   - `Features`: выбрать UI-пресет, шрифт, размер и переключатели визуальных исправлений
   - `Languages`: сменить язык контента, обновить удаленные пакеты и очистить кеш
   - `About`: обновить удаленные метаданные и проверить совместимость
6. Сохраняйте настройки после изменений. Кеш удаленных ресурсов хранится локально, пока вы не очистите его в popup.

## Сборка

Требования:

- Базовая среда выполнения: Node.js 22.
- `package-extension-zip.mjs` требует PowerShell.
- `package-crx.mjs` требует Chrome или Edge.

Команды:

1. Собрать распакованное расширение:
   `node build-extension.mjs`
2. Создать ZIP для распространения:
   `node package-extension-zip.mjs`
3. Дополнительно: создать локальный CRX:
   `node package-crx.mjs`

Результаты:

- `dist/extension/`: сгенерированное распакованное расширение
- `dist/openclaw-dashboard-plus-extension.zip`: ZIP для распространения
- `dist/openclaw-dashboard-plus.crx`: необязательный локальный CRX

## Путеводитель По Файлам

- `extension-src/`: исходники расширения, popup UI, иконки, пресеты темы и логика контента
- `extension-src/content-main.js`: исходник content script
- `extension-src/style-bundle.json`: манифест удаленно загружаемых стилевых модулей
- `extension-src/style-modules/`: модульные ресурсы CSS / HTML / JSON
- `extension-src/theme-presets.json`: встроенные определения пресетов темы
- `language-packs/`: языковые пакеты контента OpenClaw
- `ui-locales/`: строки popup UI и локализованные подписи пресетов
- `plugin-metadata.json`: канонические метаданные для версий, удаленных источников и доступных локалей
- `build-extension.mjs`: создает `dist/extension/`
- `package-extension-zip.mjs`: создает ZIP в `dist/`
- `package-crx.mjs`: помощник для локального CRX

## Установка

### ZIP Расширения

1. Скачайте `openclaw-dashboard-plus-extension.zip` из артефактов GitHub Actions или releases.
2. Распакуйте архив в стабильную папку.
3. Откройте `chrome://extensions` или `edge://extensions`.
4. Включите режим разработчика.
5. Нажмите `Load unpacked`.
6. Выберите распакованную папку.

### Локальное Распакованное Расширение

1. Выполните `node build-extension.mjs`.
2. Откройте `chrome://extensions` или `edge://extensions`.
3. Включите режим разработчика.
4. Нажмите `Load unpacked`.
5. Выберите `dist/extension/`.

## GitHub Actions

В репозитории есть workflow GitHub Actions для Windows, который автоматически:

- собирает `dist/extension/`
- создает `dist/openclaw-dashboard-plus-extension.zip`
- загружает ZIP и распакованное расширение как артефакты

## Pull Request

- Меняйте `extension-src/`, локали, метаданные или скрипты сборки. Не редактируйте `dist/extension/` напрямую.
- Репозиторий теперь только для расширения. Не возвращайте старый сценарий поставки или параллельные пути распространения.
- Удаленные ресурсы темы должны оставаться в формате HTML / CSS / JSON без исполнения JavaScript.
- Для UI или стилевых исправлений добавляйте шаги воспроизведения и при необходимости скриншоты в PR.
- Перед PR запустите соответствующую сборку и укажите результат проверки.

## Скриншоты

![Extension popup preview](../../image.png)
![Extension install preview](../../image2.png)

## Лицензия

Проект распространяется по лицензии [MIT License](../../LICENSE).
