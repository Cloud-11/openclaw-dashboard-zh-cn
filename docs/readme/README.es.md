<p align="center">
  <img src="../../icon.png" alt="Icono de OpenClaw Dashboard Plus" width="160">
</p>

# OpenClaw Dashboard Plus

Herramienta de mejora mediante extensión de navegador para OpenClaw Dashboard.

> Aviso: el desarrollador no domina el español. Este documento fue generado con ayuda de un modelo de IA y puede contener frases poco naturales.

[English](../../README.md) | [简体中文](./README.zh-CN.md) | [繁體中文](./README.zh-TW.md) | [日本語](./README.ja.md) | [한국어](./README.ko.md) | [Français](./README.fr.md) | [Español](./README.es.md) | [Русский](./README.ru.md) | [Deutsch](./README.de.md) | [Tiếng Việt](./README.vi.md) | [Filipino](./README.fil.md) | [العربية](./README.ar.md)

## Resumen

OpenClaw Dashboard Plus ahora se distribuye solo como extensión de navegador, compilada en `dist/extension/`.

El proyecto aporta:

- Configuración separada para el idioma del contenido de OpenClaw y el idioma de la interfaz popup
- Carga de metadatos, paquetes de idioma y recursos de estilo desde GitHub o Gitee
- Opciones de tema para estilo UI, fuente, tamaño de fuente y reparaciones visuales
- Una cadena unificada de iconos y metadatos para la documentación y la extensión

## Funciones

- Pestañas popup `Settings`, `Features`, `Languages` y `About`
- Actualización remota de metadatos, paquetes de idioma, presets de tema y módulos de estilo
- Entrega de recursos de tema en HTML / CSS / JSON sin JavaScript remoto
- Estructura modular que separa `extension-src/`, `language-packs/`, `ui-locales/` y `plugin-metadata.json`
- Los archivos generados se guardan en `dist/` en lugar de mezclarse con el código fuente

## Uso

1. Ejecuta `node build-extension.mjs` o descarga el ZIP generado por GitHub Actions.
2. Abre `chrome://extensions` o `edge://extensions` y activa el modo desarrollador.
3. Carga `dist/extension/` como extensión descomprimida.
4. Abre tu panel OpenClaw, por ejemplo `http://127.0.0.1:18789`.
5. Usa las pestañas del popup:
   - `Settings`: activar traducción y definir hosts y puertos permitidos
   - `Features`: elegir preset UI, fuente, tamaño y correcciones de estilo
   - `Languages`: cambiar idioma del contenido, actualizar paquetes remotos y limpiar caché
   - `About`: actualizar metadatos remotos y revisar compatibilidad o repositorio
6. Guarda la configuración después de cada cambio. Los recursos remotos en caché permanecen locales hasta borrarlos desde el popup.

## Compilación

Requisitos previos:

- Node.js 22 es el runtime de referencia.
- `package-extension-zip.mjs` requiere PowerShell.
- `package-crx.mjs` requiere Chrome o Edge.

Comandos:

1. Compilar la extensión descomprimida:
   `node build-extension.mjs`
2. Crear el ZIP de distribución:
   `node package-extension-zip.mjs`
3. Opcional: crear un CRX local:
   `node package-crx.mjs`

Salidas:

- `dist/extension/`: extensión generada sin empaquetar
- `dist/openclaw-dashboard-plus-extension.zip`: ZIP de distribución
- `dist/openclaw-dashboard-plus.crx`: CRX local opcional

## Guía De Archivos

- `extension-src/`: fuentes de la extensión, popup UI, iconos, presets de tema y lógica de contenido
- `extension-src/content-main.js`: fuente del script de contenido
- `extension-src/style-bundle.json`: manifiesto de módulos de estilo remotos
- `extension-src/style-modules/`: recursos modulares CSS / HTML / JSON
- `extension-src/theme-presets.json`: definición de presets de tema integrados
- `language-packs/`: paquetes de idioma del contenido OpenClaw
- `ui-locales/`: textos del popup y nombres o descripciones de presets
- `plugin-metadata.json`: metadatos canónicos para versiones, fuentes remotas e idiomas disponibles
- `build-extension.mjs`: construye `dist/extension/`
- `package-extension-zip.mjs`: crea el ZIP en `dist/`
- `package-crx.mjs`: ayuda opcional para CRX local

## Instalación

### ZIP De La Extensión

1. Descarga `openclaw-dashboard-plus-extension.zip` desde los artefactos de GitHub Actions o las releases.
2. Descomprímelo en una carpeta estable.
3. Abre `chrome://extensions` o `edge://extensions`.
4. Activa el modo desarrollador.
5. Haz clic en `Load unpacked`.
6. Selecciona la carpeta extraída.

### Extensión Local Descomprimida

1. Ejecuta `node build-extension.mjs`.
2. Abre `chrome://extensions` o `edge://extensions`.
3. Activa el modo desarrollador.
4. Haz clic en `Load unpacked`.
5. Selecciona `dist/extension/`.

## GitHub Actions

El repositorio incluye un flujo de GitHub Actions sobre Windows que:

- Compila `dist/extension/`
- Genera `dist/openclaw-dashboard-plus-extension.zip`
- Sube el ZIP y la extensión sin empaquetar como artefactos

## Pull Request

- Modifica `extension-src/`, las locales, los metadatos o los scripts de compilación. No edites `dist/extension/` directamente.
- El repositorio es ahora solo para la extensión. No reintroduzcas empaquetado heredado ni rutas de distribución paralelas.
- Los recursos remotos del tema deben limitarse a HTML / CSS / JSON, sin JavaScript remoto.
- Para cambios de UI o estilos, añade pasos de reproducción y, si ayuda, capturas en la PR.
- Ejecuta la compilación correspondiente antes de abrir la PR e indica el resultado de verificación.

## Capturas

![Vista previa del popup](../../image.png)
![Vista previa de instalación](../../image2.png)

## Licencia

Este proyecto se distribuye bajo la [MIT License](../../LICENSE).
