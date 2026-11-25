<h1 align="center"><img src="https://raw.githubusercontent.com/emacs-taf/etaf/main/design/etaf-logo.svg" alt="ETAF — Emacs Text Application Framework" width="480"></h1>

<p align="center">
  <a href="https://etaf.top"><img src="https://img.shields.io/badge/docs-etaf.top-7c58d6" alt="Documentation"></a>
  <a href="https://etaf.top/packages/"><img src="https://img.shields.io/badge/packages-etaf.top-7c58d6" alt="Package archive"></a>
  <img src="https://img.shields.io/badge/Emacs-29.1%2B-7c58d6" alt="Emacs 29.1 or later">
  <a href="#license"><img src="https://img.shields.io/badge/license-GPL--3.0-blue" alt="License: GPL-3.0 or later"></a>
  <a href="https://t.me/vhkdzszh"><img src="https://img.shields.io/badge/Telegram-@vhkdzszh-26A5E4?logo=telegram&logoColor=white" alt="Telegram channel"></a>
  <a href="https://t.me/+4X48uOJC0KBkOWY1"><img src="https://img.shields.io/badge/Group-Telegram-26A5E4?logo=telegram&logoColor=white" alt="Telegram group"></a>
  <a href="https://www.youtube.com/channel/UChv8vFXjDfs8MeNdEkff1jg"><img src="https://img.shields.io/badge/YouTube-Demos-FF0000?logo=youtube&logoColor=white" alt="YouTube channel"></a>
</p>

**ETAF** (Emacs Text Application Framework) builds complete text applications in Emacs with a web-style model: declarative components and reactive state, CSS cascade styling, Box/Flex/Grid layout, and incremental buffer updates instead of full redraws. Around it sit a shared UI catalog, data and child-frame hosts, an official `package.el` archive at [etaf.top/packages](https://etaf.top/packages/), and a growing suite of native Emacs applications and games.

> **Status.** ETAF is under active development and framework APIs may still evolve. Packages published in the [official package archive](https://etaf.top/packages/) (`M-x etaf-install`) are prepared for daily use; repositories listed under *In development* are still being built or available from source checkouts only.

**[Install](#install)** · **[Framework](#framework)** · **[Applications](#applications)** · **[Games](#games)** · **[First View](#first-view)** · **[Documentation](#documentation)** · **[Development](#development)** · **[Community](#community)** · **[License](#license)**

## Install

ETAF runs on Emacs 29.1 or later. Evaluate this once in your existing Emacs, then choose any framework package, application or game (the component gallery is the default):

```elisp
;;; -*- lexical-binding: t; -*-
(require 'package)
(add-to-list 'package-archives '("etaf" . "https://etaf.top/packages/"))
(package-initialize)
(package-refresh-contents)
(package-install 'etaf-install)
(call-interactively #'etaf-install)
```

Afterward, use `M-x etaf-install` to open or install targets, `M-x etaf-install-manage` to inspect versions, update or remove packages, and `M-x etaf-install-doctor` to check optional runtime capabilities. `package.el` owns dependency resolution, byte compilation, updates and removal; no Git, Python, system compiler or replacement Emacs configuration is required for pure-Lisp targets. Browse published releases at [etaf.top/packages](https://etaf.top/packages/) or read the [installation reference](https://etaf.top/introduction/#installation).

## Framework

The framework is layered and each package owns one concern: ECSS computes styles, EKP breaks paragraphs, Ebox lays out and incrementally publishes text, and ETAF adds components, reactive state and application services. Every package keeps its own public interface, checks and releases (`etaf-install` ships from [emacs-taf](https://github.com/emacs-taf/emacs-taf)).

| Package | Role |
| --- | --- |
| [ecss](https://github.com/emacs-taf/ecss) | CSS cascade engine: selectors, specificity, custom properties and computed styles |
| [ekp](https://github.com/emacs-taf/ekp) | Knuth–Plass paragraph line breaking, with an optional threaded C module |
| [ebox](https://github.com/emacs-taf/ebox) | Box/Flex/Grid layout, rendering and incremental buffer updates |
| [etaf](https://github.com/emacs-taf/etaf) | Components, reactive state, hosts and the application lifecycle |
| [etaf-ui](https://github.com/emacs-taf/etaf-ui) | Reusable UI components: buttons, forms, panels, tables, navigation and window shells |
| [etaf-posframe](https://github.com/emacs-taf/etaf-posframe) | Floating child-frame panels for any ETAF View: title bar, theme modes and edge resizing |
| [etaf-db](https://github.com/emacs-taf/etaf-db) | Data backends for ETAF applications; SQLite today |
| [etaf-gamekit](https://github.com/emacs-taf/etaf-gamekit) | Game definitions, independent instances, actions and backend adapters (Godot, boardgame.io, OpenSpiel) |
| [etaf-manual](https://github.com/emacs-taf/etaf-manual) | Bilingual ETAF Reference Manual (87 chapters, verified against public APIs) and in-Emacs reader (`M-x etaf-manual-open`) |

## Applications

Applications are independent programs built on the framework; each publishes as its own repository with its own version, README and checks.

### Available via `etaf-install`

These applications are published in the [official package archive](https://etaf.top/packages/) and ready for daily use:

| Application | Description |
| --- | --- |
| [etaf-md](https://github.com/emacs-taf/etaf-md) | Native Markdown reader & live preview: zero-browser Mermaid & MathJax SVGs, 35+ doc containers, living-doc widgets, full-grid tables and media in one buffer |
| [etaf-org-preview](https://github.com/emacs-taf/etaf-org-preview) | Modern Org reading view: centered measure, heading ladder, keyword/priority chips, planning lines, tables, code blocks, callouts, images and TOC |
| [maillist](https://github.com/emacs-taf/maillist) | Mailing-list client: public-inbox threads, unread/starred scopes, fixed-header reader, local SQLite state and `smtpmail` replies |
| [etaf-video-player](https://github.com/emacs-taf/etaf-video-player) | Local video and streams as sharp image frames, density characters or true-color half blocks, with sound |
| [etaf-ncm](https://github.com/emacs-taf/etaf-ncm) | NetEase Cloud Music player: library browsing, playback control, lyrics and queue |
| [etaf-weread](https://github.com/emacs-taf/etaf-weread) | WeChat Reading client: shelf, notebook, highlights, store search and statistics |
| [etaf-telega](https://github.com/emacs-taf/etaf-telega) | Telegram client on Telega's TDLib backend: chats, live message stream, composer and message actions |
| [etaf-desktop](https://github.com/emacs-taf/etaf-desktop) | Desktop manager: windows, workspaces, focus order and z-order |
| [etaf-pomodoro](https://github.com/emacs-taf/etaf-pomodoro) | Focus timer as a window or a floating panel: reactive countdown, three styles and a host-following palette |

### In development

These applications are under active development or currently available from source checkouts only; they are not in the package archive yet.

| Application | Description |
| --- | --- |
| [etaf-rss](https://github.com/emacs-taf/etaf-rss) | RSS reader: subscriptions, folders, unread and starred scopes, reading pane, search and OPML |
| [etaf-reader](https://github.com/emacs-taf/etaf-reader) | Local ebook reader: EPUB/TXT/Markdown/HTML/FB2/PDF import, paged reading, annotations and progress |
| [etaf-bili](https://github.com/emacs-taf/etaf-bili) | Bilibili client: popular feed, ranking and search with in-buffer playback |
| [etaf-youtube](https://github.com/emacs-taf/etaf-youtube) | YouTube client: account feeds, search, channels, playlists, comments and in-canvas video playback |
| [etaf-ascii-video](https://github.com/emacs-taf/etaf-ascii-video) | Pure-character video and HTTP(S) stream viewer (density ramp and true-color half blocks) |
| [etaf-screensaver](https://github.com/emacs-taf/etaf-screensaver) | Generative pure-Elisp idle screensavers for Emacs |
| [etaf-slides](https://github.com/emacs-taf/etaf-slides) | Markdown slide deck presenter: aspect-preserving 16:9 stage, speaker notes and presentation clock |
| [etaf-pi](https://github.com/emacs-taf/etaf-pi) | Native Pi agent client: streamed conversations, tool output, session recovery and multiline input |
| [etaf-video-studio](https://github.com/emacs-taf/etaf-video-studio) | Record, edit and publish software tutorials from an ETAF text workbench |
| [etaf-algo-lab](https://github.com/emacs-taf/etaf-algo-lab) | Learn algorithms by watching, steering and comparing them inside Emacs |

## Games

Games keep their rules, presentation and resources in their own repositories and build on [etaf-gamekit](https://github.com/emacs-taf/etaf-gamekit):

| Game | Description | Backend | Availability |
| --- | --- | --- | --- |
| [etaf-xiangqi](https://github.com/emacs-taf/etaf-xiangqi) | Chu He: xiangqi (Chinese chess) against the computer or hot-seat | OpenSpiel | `etaf-install` |
| [etaf-tanks](https://github.com/emacs-taf/etaf-tanks) | Iron Tide: real-time tank battle with a native arena | Godot | `etaf-install` |
| [etaf-solitaire](https://github.com/emacs-taf/etaf-solitaire) | Verdant: K+ Klondike solitaire with undo and redo | OpenSpiel | Source checkout |
| [etaf-salvage](https://github.com/emacs-taf/etaf-salvage) | Salvage Station: real-time exploration and extraction | Godot | Source checkout |

## First View

After installing `etaf` (or cloning `ecss`, `ebox` and `etaf` onto `load-path`), evaluate this snippet, switch to `*etaf-hello*` and activate the button:

```elisp
;;; -*- lexical-binding: t; -*-
(require 'etaf)

(etaf-mount
 "*etaf-hello*"
 (etaf-view
  (column
    (text :font-weight 'bold "Hello")
    (box :ref 'hello :role 'button :tab-index 0
         :on-press (lambda () (message "Hello ETAF"))
      "Say hello"))))
```

When developing from source checkouts, `make compile` byte-compiles a repository and `make check` runs its structure, compilation, public API boundary and acceptance checks.

## Documentation

- [etaf.top](https://etaf.top) publishes the full ETAF Reference Manual (English at `/`, Simplified Chinese at [`/zh-cn/`](https://etaf.top/zh-cn/)) and the browsable [package archive](https://etaf.top/packages/).
- [etaf-manual](https://github.com/emacs-taf/etaf-manual) holds the book source (87 chapters covering `ecss`, `ekp`, `ebox`, `etaf`, `etaf-ui` and `etaf-db`, checked against live public interfaces) and the in-Emacs reader (`M-x etaf-manual-open`).
- Each package's `README.md` and root entry Commentary document its supported public API, signatures, lifecycle and usage notes.

## Development

- [emacs-taf](https://github.com/emacs-taf/emacs-taf) owns the workspace orchestration, `etaf-install`, repository map and the shared [architecture and development contract](https://github.com/emacs-taf/emacs-taf/blob/main/docs/architecture.zh-CN.md).
- [etaf-playground](https://github.com/emacs-taf/etaf-playground) and [ebox-playground](https://github.com/emacs-taf/ebox-playground) hold runnable integration examples and acceptance surfaces.

Each repository runs its own public checks (`make check`). Issues and pull requests are welcome in the repository they concern.

## Community

- **Telegram channel**: [@vhkdzszh](https://t.me/vhkdzszh) — release announcements and demos.
- **Telegram group**: [ETAF Group](https://t.me/+4X48uOJC0KBkOWY1) — discussion, questions and feedback.
- **YouTube**: [ETAF YouTube Channel](https://www.youtube.com/channel/UChv8vFXjDfs8MeNdEkff1jg) — video demos and walkthroughs.
- **Maintainer**: [@geekinney](https://t.me/geekinney).

## License

Each repository is licensed under the GNU General Public License v3.0 or later ([GPL-3.0-or-later](https://github.com/emacs-taf/etaf/blob/main/LICENSE)).
