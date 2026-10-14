<h1 align="center"><img src="https://raw.githubusercontent.com/emacs-taf/etaf/main/design/etaf-logo.svg" alt="ETAF — Emacs Text Application Framework" width="480"></h1>

<p align="center">
  <a href="https://etaf.top"><img src="https://img.shields.io/badge/docs-etaf.top-7c58d6" alt="Documentation"></a>
  <a href="#license"><img src="https://img.shields.io/badge/license-GPL--3.0-blue" alt="License: GPL-3.0 or later"></a>
  <img src="https://img.shields.io/badge/Emacs-29.1%2B-7c58d6" alt="Emacs 29.1 or later">
</p>

**ETAF** builds complete text applications in Emacs with a web-style model:
declarative components and reactive state, CSS cascade styling, Box/Flex/Grid
layout, and incremental buffer updates instead of full redraws. Around it sit a
shared UI catalog, data backends, and a growing set of applications — a music
player, readers, chat and video clients.

> **Status.** ETAF is under active development, and its interfaces may still
> change. The applications listed under *In development* are still being built
> and are not recommended for daily use yet; the other applications and games
> are prepared for daily use.

**[Framework](#framework)** · **[Applications](#applications)** · **[Games](#games)** · **[Get started](#get-started)** · **[Documentation](#documentation)** · **[Development](#development)** · **[License](#license)**

## Framework

The framework is layered and each package owns one concern: ECSS computes
styles, EKP breaks paragraphs, Ebox lays out and publishes text, and ETAF adds
components, state and application services. Every package keeps its own public
interface, checks and releases.

| Package | Function |
| --- | --- |
| [ecss](https://github.com/emacs-taf/ecss) | CSS cascade engine: selectors, specificity, custom properties and computed styles |
| [ekp](https://github.com/emacs-taf/ekp) | Knuth–Plass paragraph line breaking, with an optional threaded C module |
| [ebox](https://github.com/emacs-taf/ebox) | Box/Flex/Grid layout, rendering and incremental buffer updates |
| [etaf](https://github.com/emacs-taf/etaf) | Components, reactive state, hosts and the application lifecycle |
| [etaf-ui](https://github.com/emacs-taf/etaf-ui) | Reusable UI components: buttons, forms, panels and window shells |
| [etaf-db](https://github.com/emacs-taf/etaf-db) | Data backends for ETAF applications; SQLite today |

Games also use [etaf-gamekit](https://github.com/emacs-taf/etaf-gamekit),
which bridges game definitions, independent instances and a common
action/observation lifecycle to Godot, boardgame.io and OpenSpiel.

## Applications

Applications are independent programs built on the framework; each has its own
repository, history and checks, and installs the framework packages it needs.

### Ready for daily use

| Application | Function |
| --- | --- |
| [etaf-video-player](https://github.com/emacs-taf/etaf-video-player) | Local video and streams as sharp image frames with sound |
| [etaf-ncm](https://github.com/emacs-taf/etaf-ncm) | NetEase Cloud Music player: library browsing, playback control, lyrics and queue |
| [etaf-weread](https://github.com/emacs-taf/etaf-weread) | WeChat Reading client: shelf, notebook, highlights, store search and statistics |
| [etaf-md-preview](https://github.com/emacs-taf/etaf-md-preview) | Markdown reading view: centered measure, headings, tables, callouts, code and media cards |
| [etaf-telega](https://github.com/emacs-taf/etaf-telega) | Telegram client on Telega's TDLib backend: chats, live message stream, composer and message actions |
| [etaf-desktop](https://github.com/emacs-taf/etaf-desktop) | Desktop manager: windows, workspaces, focus order and z-order |
| [etaf-ascii-video](https://github.com/emacs-taf/etaf-ascii-video) | Video and HTTP(S) streams inside an Emacs buffer as pure characters |

### In development

These applications are under active development; expect rough edges, missing
features or breaking changes, and do not rely on them for daily work yet.

| Application | Function |
| --- | --- |
| [etaf-rss](https://github.com/emacs-taf/etaf-rss) | RSS reader: subscriptions, folders, unread and starred scopes, reading pane, search and OPML |
| [etaf-reader](https://github.com/emacs-taf/etaf-reader) | Local ebook reader: EPUB/TXT/Markdown/HTML/FB2/PDF import, paged reading, annotations and progress |
| [etaf-pi](https://github.com/emacs-taf/etaf-pi) | Native Pi agent client: streamed conversations, tool output, session recovery and multiline input |
| [etaf-bili](https://github.com/emacs-taf/etaf-bili) | Bilibili client: popular feed, ranking and search with in-buffer playback |
| [etaf-video-studio](https://github.com/emacs-taf/etaf-video-studio) | Record, edit and publish software tutorials through the video-project skill |
| [etaf-algo-lab](https://github.com/emacs-taf/etaf-algo-lab) | Learn algorithms by watching, steering and comparing them inside Emacs |

## Games

Games keep their rules, presentation and resources in their own repositories
and build on [etaf-gamekit](https://github.com/emacs-taf/etaf-gamekit):

| Game | Description | Backend |
| --- | --- | --- |
| [etaf-solitaire](https://github.com/emacs-taf/etaf-solitaire) | Verdant: K+ Klondike solitaire with undo and redo | OpenSpiel |
| [etaf-xiangqi](https://github.com/emacs-taf/etaf-xiangqi) | Chu He: xiangqi (Chinese chess) against the computer or hot-seat | OpenSpiel |
| [etaf-tanks](https://github.com/emacs-taf/etaf-tanks) | Iron Tide: real-time tank battle with a native arena | Godot |
| [etaf-salvage](https://github.com/emacs-taf/etaf-salvage) | Salvage Station: real-time exploration and extraction | Godot |

## Get started

ETAF runs on Emacs 29.1 or later (ECSS alone needs 28.1). Clone the packages you
use as sibling directories and add each repository root to `load-path`:

```sh
git clone https://github.com/emacs-taf/ecss.git
git clone https://github.com/emacs-taf/ebox.git
git clone https://github.com/emacs-taf/etaf.git
```

```elisp
(add-to-list 'load-path "/path/to/ecss")
(add-to-list 'load-path "/path/to/ebox")
(add-to-list 'load-path "/path/to/etaf")

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

Evaluate it, switch to `*etaf-hello*` and activate the button. `make compile`
byte-compiles a checkout, and ETAF and Ebox also build native code with
`make native`. The manual's
[installation chapter](https://etaf.top/installation-and-loading/) covers
package.el installation, optional programs, icon fonts and terminal-frame
behavior.

## Documentation

- [etaf.top](https://etaf.top) is the published reference manual: English at the
  root, Simplified Chinese at [`/zh-cn/`](https://etaf.top/zh-cn/). It documents
  every public interface of ECSS, EKP, Ebox, ETAF, ETAF UI and ETAF DB, and its
  examples mount and run in place.
- [etaf-manual](https://github.com/emacs-taf/etaf-manual) holds the book source
  and the in-Emacs reader; `M-x etaf-manual-open` opens the manual in a buffer.
- Each package's README and root entry Commentary document its own supported
  API, calling signatures and usage notes.

## Development

- [emacs-taf](https://github.com/emacs-taf/emacs-taf) records the repository
  map, integration checkpoints and the shared engineering rules; read the
  [architecture and development contract](https://github.com/emacs-taf/emacs-taf/blob/main/docs/architecture.zh-CN.md)
  before cross-package work.
- [etaf-apps](https://github.com/emacs-taf/etaf-apps) and
  [etaf-games](https://github.com/emacs-taf/etaf-games) are the application and
  game workspaces with their own checkpoints and shared tooling.
- [etaf-playground](https://github.com/emacs-taf/etaf-playground) and
  [ebox-playground](https://github.com/emacs-taf/ebox-playground) hold runnable
  examples and acceptance surfaces.

Each repository runs its own checks (`make check`); the workspace repositories
orchestrate them in dependency order. Issues and pull requests are welcome in
the repository they concern.

## License

Each repository is licensed under the GNU General Public License v3.0 or later
([GPL-3.0-or-later](https://github.com/emacs-taf/etaf/blob/main/LICENSE)).
