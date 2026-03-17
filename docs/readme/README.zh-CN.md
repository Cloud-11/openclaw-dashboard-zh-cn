<p align="center">
  <img src="../../icon.png" alt="OpenClaw Dashboard Plus 图标" width="160">
</p>

# OpenClaw Dashboard Plus

以浏览器扩展为主、附带中文翻译用户脚本的 OpenClaw Dashboard 工具集。

[English](../../README.md) | [简体中文](./README.zh-CN.md) | [繁體中文](./README.zh-TW.md) | [日本語](./README.ja.md) | [한국어](./README.ko.md) | [Français](./README.fr.md) | [Español](./README.es.md) | [Русский](./README.ru.md) | [Deutsch](./README.de.md) | [Tiếng Việt](./README.vi.md) | [Filipino](./README.fil.md) | [العربية](./README.ar.md)

## 概述

项目提供两种使用方式，其中扩展为主：

- 构建输出到 `dist/extension/` 的浏览器扩展
- `openclaw-dashboard-plus-zh.user.js` 中文翻译用户脚本

浏览器扩展是当前主形态；用户脚本保留为较轻量的中文翻译入口，适合不方便安装扩展的场景。

## 功能

- 内容语言与扩展面板语言分离
- 支持从 GitHub / Gitee 拉取元信息与语言包
- 扩展弹窗可管理运行时设置、缓存与版本信息
- 提供主题预设、字体、字号和独立样式修补开关
- 远程样式模块仅拉取 HTML / CSS / JSON，不引入远程 JavaScript
- 文档与浏览器扩展统一使用同一套项目图标
- 生成产物集中输出到 `dist/`，避免源码与构建结果混放

## 使用方式

1. 运行 `node build-extension.mjs` 构建扩展，或者直接下载 GitHub Actions 产出的 ZIP。
2. 在 `chrome://extensions` 或 `edge://extensions` 开启开发者模式，加载 `dist/extension/`。
3. 打开本地 OpenClaw 面板，例如 `http://127.0.0.1:18789`。
4. 在扩展弹窗中使用各页签：
   - `设置`：启用翻译、配置生效主机和端口。
   - `功能`：选择 OpenClaw UI 预设、字体、字号，并单独切换样式覆盖、样式修补、下拉框修复、代码块样式修补。
   - `语言`：切换 OpenClaw 内容语言、下载远端语言包、清理缓存。
   - `关于`：刷新远端元信息，查看当前扩展版本与 OpenClaw 兼容信息。
5. 修改后分别保存运行配置或主题配置。远端主题和样式资源下载后会缓存到本地，直到手动清理。

## 构建

前置要求：

- 推荐使用 Node.js 22，与 GitHub Actions 工作流保持一致。
- `package-extension-zip.mjs` 依赖 PowerShell。
- `package-crx.mjs` 需要本机安装 Chrome 或 Edge。

常用命令：

1. 生成解压扩展：
   `node build-extension.mjs`
2. 打包浏览器扩展 ZIP：
   `node package-extension-zip.mjs`
3. 如需本地 CRX：
   `node package-crx.mjs`

产物目录：

- `dist/extension/`：生成后的解压扩展目录
- `dist/openclaw-dashboard-plus-extension.zip`：发布用 ZIP 包
- `dist/openclaw-dashboard-plus.crx`：可选的本地 CRX 包

## 功能文件说明

- `extension-src/`：扩展源码、弹窗 UI、图标和内容脚本补丁
- `extension-src/style-bundle.json`：远程可拉取样式模块清单
- `extension-src/style-modules/`：按模块组织的 CSS / HTML / JSON 样式资源
- `language-packs/`：OpenClaw 内容语言包
- `ui-locales/`：扩展面板多语言文案
- `theme-presets.json`：内置主题预设定义
- `plugin-metadata.json`：仓库元信息、兼容版本、远端拉取源配置
- `build-extension.mjs`：生成 `dist/extension/` 并同步打包资源
- `package-extension-zip.mjs`：生成 `dist/` 下的扩展 ZIP
- `package-crx.mjs`：本地 CRX 打包脚本
- `dist/extension/`：构建产物目录，不应手工直接修改
- `openclaw-dashboard-plus-zh.user.js`：保留的中文翻译用户脚本入口

## 安装

### 用户脚本

1. 打开 `openclaw-dashboard-plus-zh.user.js`
2. 使用 Tampermonkey、ScriptCat 或兼容的用户脚本管理器安装

### 浏览器扩展 ZIP

1. 从 GitHub Actions 构建产物或 Releases 下载 `openclaw-dashboard-plus-extension.zip`
2. 解压到固定目录
3. 打开 `chrome://extensions` 或 `edge://extensions`
4. 开启开发者模式
5. 点击“加载已解压的扩展程序”
6. 选择解压后的目录

### 本地解压扩展

1. 运行 `node build-extension.mjs`
2. 打开 `chrome://extensions` 或 `edge://extensions`
3. 开启开发者模式
4. 点击“加载已解压的扩展程序”
5. 选择 `dist/extension/`

## GitHub Actions

仓库内置了基于 Windows 的 GitHub Actions 工作流，会自动：

- 构建 `dist/extension/`
- 打包 `dist/openclaw-dashboard-plus-extension.zip`
- 上传 ZIP 与解压扩展作为工作流产物

## PR 说明

- 请优先修改 `extension-src/`、语言资源、元信息文件或构建脚本，不要直接手改 `dist/extension/`。
- 仓库以浏览器扩展为主形态；除非确实需要维护用户脚本，否则不要顺手改 `openclaw-dashboard-plus-zh.user.js`。
- 远程拉取的主题资源请保持为 HTML / CSS / JSON，不要新增远程 JavaScript 执行路径。
- 涉及弹窗 UI、OpenClaw 样式或交互修复时，请在 PR 描述里附上复现步骤，并尽量补充截图。
- 提交前至少运行对应构建命令，并在 PR 描述中写明验证结果。
- 用户可见行为发生变化时，优先更新英文主 README，再同步中文或其他语言文档。

## 截图

![扩展弹窗示意图](../../image.png)
![扩展安装示意图](../../image2.png)

## 许可证

本项目使用 [MIT License](../../LICENSE)。
