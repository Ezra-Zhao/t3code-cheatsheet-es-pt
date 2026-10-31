# T3 Code 速查表 | T3 Code Cheatsheet | Guía rápida de T3 Code

> 一页看懂 T3 Code：装在你自己机器上的一层「agent 遥控台」——Claude Code、Codex、Cursor 等编程 agent 仍然在你的电脑上跑、仍然花你自己的订阅，你用手机 App、网页或桌面端从任何地方看它们干活、给它们派活。它自己不卖模型，甚至明说：哪天我们走偏了，你把仓 fork 走自己建。

- 上游项目：[pingdotgg/t3code](https://github.com/pingdotgg/t3code)（2026-10-31 实测 35,175 ★ / 8,767 forks，765 个 release，MIT）
- 平台：服务端跑在你自己的机器上（Windows / macOS / Linux）；控制端有 iOS / Android App、网页版（app.t3.codes）与 Electron 桌面端（t3.codes）
- 本页结构：中文主文 → English → Español → Português

---

Apoyo y más: [GitHub Sponsors](https://github.com/sponsors/Ezra-Zhao) · [Gumroad — plantillas y cuadernos que uso](https://ezraflow28.gumroad.com) · [Ko-fi](https://ko-fi.com/ezra777zhao)

## 它是什么、不是什么

| 是 | 不是 |
|---|---|
| 已装 agent 的控制面（control surface）：会话、派活、盯进度、批权限都收进一个界面 | 不是新的 agent：它不写代码，写代码的是你本机那些 CLI |
| 用你已有的订阅：各 agent 在你电脑上装好并登录好，它就能接管控制 | 不卖额度、不中转 API：模型账单还是各家自己的 |
| 远程就绪：手机 App 是它的一等公民，出门在外也能盯长任务 | 不是云服务：服务器就是你那台机器，它关机/断网就遥控不了 |

## 支持的 agent 与登录命令（前置条件，缺一不可）

用之前，本机至少装好并登录一个 provider，否则 T3 Code 装上也是空壳：

| Provider | 先装 | 再登录 |
|---|---|---|
| Codex | Codex CLI | `codex login` |
| Claude Code | Claude Code | `claude auth login` |
| Cursor | Cursor CLI | `agent login` |
| Grok Build | Grok Build CLI | `grok login` |
| OpenCode | OpenCode | `opencode auth login` |
| Google Antigravity | 无需 CLI | 在 T3 Code 的 Settings 里启用，用 Install Antigravity 并以 Google 账号登录 |

## 安装一行版

命令行版（起服务端＋本机网页版）：

| 平台 | 命令 |
|---|---|
| macOS / Linux | `curl -fsSL https://t3.codes/install.sh \| sh` |
| Windows（PowerShell） | `irm https://t3.codes/install.ps1 \| iex` |
| 免安装试用一次 | `npx t3@latest` |

装完的日常三条：`t3` 启动服务端并打开本机网页版；`t3 service install` 把它装成后台常驻服务；`t3 update` 升级到新版；完整命令看 `t3 --help`。

桌面端：

| 渠道 | 命令／入口 |
|---|---|
| GitHub Releases | 下最新版安装包装 |
| Windows（winget） | `winget install T3Tools.T3Code` |
| Windows（scoop） | `scoop install extras/t3code` |
| macOS（Homebrew） | `brew install --cask t3-code` |
| Debian / Ubuntu | Releases 下 `.deb`，`sudo apt install ./T3-Code-*.deb` |
| Arch（AUR） | 稳定版 `yay -S t3code-bin`；nightly `yay -S t3code-nightly-bin` |
| Nix（nixpkgs） | `nix profile add github:NixOS/nixpkgs/nixos-unstable#t3code`（含桌面端与 `t3` 命令） |

## 上手四步卡

1. **先备好一个 agent**：按上表装 CLI 并跑通登录命令，在终端里确认它能独立工作，再回头装 T3 Code——排障时先分清问题出在哪一层。
2. **本机先跑通**：`t3` 起服务，在本机网页版里确认能看到会话、能派一个小任务、权限弹窗能批。
3. **再开远程**：手机装 App，按上游文档的远程访问说明把手机与本机服务连上；权限模式（permission modes）先看一遍仓内文档再开远程，别裸奔。
4. **转常驻**：确认日常都顺手了，再 `t3 service install` 让它开机常驻，省得每次手起。

## 文档地图（都在上游仓 docs/ 里，没有独立文档站）

FAQ、Install and first run、Permission modes、Keyboard shortcuts、Project settings、Appearance preferences、Remote access（手机/异机远程）、Connect agents over MCP、Keeping app and server in sync、Source control integrations、Multiple accounts（Codex / Claude 多账号）、Run as a background service。遇到具体问题先翻对应那篇，比在 issue 里翻聊天记录快。

## 诚实标注区

- **官方自称非常早期**：原话「very very early，expect bugs」；765 个 release 说明迭代极快，但也意味着界面与行为会变，本页口径是 2026-10-31 的。
- **暂不怎么收贡献**：官方说大功能不收、小修可能考虑——想提需求走 Ideas discussion，想要的功能更可能要自己 fork。
- **它只做控制，不做兜底**：agent 本身的订阅、额度、封号风险都是你和各 provider 之间的事，T3 Code 不参与也不担保。
- **远程＝把本机控制权开个口**：能从手机批权限、派任务，反过来说账号与连接的安全就是你代码仓库的安全；权限模式先设好，公共网络下别图省事全放行。
- **机器必须醒着**：服务端跑在你自己的机器上，合盖睡眠、断网、关机都会断线；长任务出门前，先确认电源与睡眠设置。

---

## English (summary)

T3 Code (by pingdotgg, ~35.2k stars as of 2026-10-31, MIT) is an "agent harness control surface": the coding agents stay on your machine and keep billing your own subscriptions, while T3 Code gives you a best-in-class mobile app (iOS/Android), a web app (app.t3.codes), and an Electron desktop app to watch and steer them from anywhere. It sells nothing — control only.

It works with Claude Code, Codex, Cursor, Grok Build, OpenCode, and Google Antigravity — but only with providers you have already installed and authenticated on that machine (`codex login`, `claude auth login`, `agent login`, `grok login`, `opencode auth login`; Antigravity is enabled in Settings with Google sign-in, no CLI). Install the CLI with `curl -fsSL https://t3.codes/install.sh | sh` (PowerShell: `irm https://t3.codes/install.ps1 | iex`), run `t3`, keep it resident with `t3 service install`, upgrade with `t3 update`, or try it once via `npx t3@latest`. Desktop builds come from GitHub Releases, winget, scoop, Homebrew cask, .deb, the AUR, and nixpkgs.

Honest notes: the project calls itself "very very early — expect bugs"; contributions are mostly closed (small fixes only); docs live in the repo's docs/ folder, no docs site yet; and remote access means your machine must stay awake and your permission modes deserve a careful read before you open it up to your phone.

---

## Español (guía rápida — traducción de estudio, pendiente de revisión por un hablante nativo)

T3 Code (de pingdotgg, ~35,2 mil estrellas en octubre de 2026, MIT) es una «superficie de control» para agentes de código: los agentes siguen corriendo en tu máquina y gastando tus propias suscripciones, y T3 Code te da una app móvil (iOS/Android), una app web (app.t3.codes) y una app de escritorio Electron para vigilarlos y dirigirlos desde cualquier lugar. No vende nada: solo control.

**Requisito previo**: funciona con Claude Code, Codex, Cursor, Grok Build, OpenCode y Google Antigravity, pero solo con los proveedores que ya tengas instalados y autenticados en esa máquina: `codex login`, `claude auth login`, `agent login`, `grok login`, `opencode auth login`. Antigravity se activa en Settings con la cuenta de Google, sin CLI.

**Instalación (CLI)**: en macOS/Linux, `curl -fsSL https://t3.codes/install.sh | sh`; en Windows PowerShell, `irm https://t3.codes/install.ps1 | iex`. Después: `t3` arranca el servidor y abre la web local, `t3 service install` lo deja corriendo en segundo plano, `t3 update` actualiza, y `npx t3@latest` sirve para probarlo sin instalar. Escritorio: GitHub Releases, `winget install T3Tools.T3Code`, `scoop install extras/t3code`, `brew install --cask t3-code`, paquete .deb, AUR (`t3code-bin`) o nixpkgs.

**Puesta en marcha**: primero deja un agente funcionando por su cuenta en la terminal; luego verifica en la web local que ves las sesiones y puedes aprobar permisos; después conecta el móvil siguiendo la guía de acceso remoto (lee antes los modos de permiso); y solo al final déjalo como servicio permanente.

**Notas honestas**: el propio proyecto se declara «muy, muy temprano: espera errores»; apenas acepta contribuciones (solo arreglos pequeños); la documentación vive en la carpeta docs/ del repositorio, sin sitio propio todavía; y el acceso remoto exige que tu máquina esté despierta — y que trates la seguridad de la conexión como la seguridad de tu código.

---

## Português (guia rápido — tradução de estudo, aguardando revisão de um falante nativo)

O T3 Code (do pingdotgg, ~35,2 mil estrelas em outubro de 2026, MIT) é uma «superfície de controle» para agentes de código: os agentes continuam rodando na sua máquina e gastando as suas próprias assinaturas, e o T3 Code oferece um app móvel (iOS/Android), um app web (app.t3.codes) e um app desktop Electron para acompanhar e comandar tudo de qualquer lugar. Não vende nada: é só controle.

**Pré-requisito**: funciona com Claude Code, Codex, Cursor, Grok Build, OpenCode e Google Antigravity, mas apenas com os provedores já instalados e autenticados naquela máquina: `codex login`, `claude auth login`, `agent login`, `grok login`, `opencode auth login`. O Antigravity é ativado nas Settings com a conta Google, sem CLI.

**Instalação (CLI)**: no macOS/Linux, `curl -fsSL https://t3.codes/install.sh | sh`; no Windows PowerShell, `irm https://t3.codes/install.ps1 | iex`. Depois: `t3` sobe o servidor e abre a web local, `t3 service install` deixa rodando em segundo plano, `t3 update` atualiza, e `npx t3@latest` serve para testar sem instalar. Desktop: GitHub Releases, `winget install T3Tools.T3Code`, `scoop install extras/t3code`, `brew install --cask t3-code`, pacote .deb, AUR (`t3code-bin`) ou nixpkgs.

**Primeiros passos**: primeiro deixe um agente funcionando sozinho no terminal; depois confirme na web local que você enxerga as sessões e consegue aprovar permissões; em seguida conecte o celular seguindo o guia de acesso remoto (leia os modos de permissão antes); e só no fim deixe como serviço permanente.

**Notas honestas**: o próprio projeto se declara «muito, muito no início: espere bugs»; quase não aceita contribuições (só correções pequenas); a documentação mora na pasta docs/ do repositório, ainda sem site próprio; e o acesso remoto exige que a sua máquina fique acordada — e que você trate a segurança da conexão como a segurança do seu código.

---

## 来源与声明

- 灵感来源 / Source / Fuente / Fonte: [pingdotgg/t3code](https://github.com/pingdotgg/t3code)（官网 t3.codes）
- 本仓是个人学习整理：内容用我自己的话总结自上游公开文档，不搬运原文；支持名单与安装命令以 2026-10-31 的上游 README 为准，上游迭代很快，请以官方文档为最终依据。
- 西语、葡语部分为学习译稿，待母语校对。Las secciones en español y portugués son traducciones de estudio pendientes de revisión nativa.
- License: MIT © 2026 Guangyi Zhao
