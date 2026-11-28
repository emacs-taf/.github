<h1 align="center"><img src="https://raw.githubusercontent.com/emacs-taf/emacs-taf/main/core/packages/etaf/design/etaf-logo.svg" alt="ETAF — Emacs Text Application Framework" width="420"></h1>

<p align="center">
  <a href="https://github.com/emacs-taf/emacs-taf"><img src="https://img.shields.io/badge/monorepo-emacs--taf-2ea44f" alt="Monorepo"></a>
  <a href="https://github.com/emacs-taf/etaf"><img src="https://img.shields.io/badge/core-etaf-7c58d6" alt="Core Framework"></a>
  <a href="https://etaf.top"><img src="https://img.shields.io/badge/docs-etaf.top-7c58d6" alt="Documentation"></a>
  <a href="https://etaf.top/packages/"><img src="https://img.shields.io/badge/packages-etaf.top-7c58d6" alt="Package archive"></a>
  <a href="https://etaf.top/native/"><img src="https://img.shields.io/badge/native-etaf.top-7c58d6" alt="Prebuilt native modules"></a>
  <a href="https://etaf.top/media/"><img src="https://img.shields.io/badge/media-etaf.top-7c58d6" alt="Media library"></a>
  <img src="https://img.shields.io/badge/Emacs-29.1%2B-7c58d6" alt="Emacs 29.1+">
  <a href="https://t.me/vhkdzszh"><img src="https://img.shields.io/badge/Telegram-@vhkdzszh-26A5E4?logo=telegram&logoColor=white" alt="Telegram channel"></a>
  <a href="https://t.me/+4X48uOJC0KBkOWY1"><img src="https://img.shields.io/badge/Group-Telegram-26A5E4?logo=telegram&logoColor=white" alt="Telegram group"></a>
</p>

**ETAF** (Emacs Text Application Framework) brings a web-style declarative component model, CSS cascade styling, Box/Flex/Grid layout and incremental buffer updates to native Emacs applications and games.

- **Development & PRs**: **[emacs-taf/emacs-taf](https://github.com/emacs-taf/emacs-taf)** — the official monorepo (`core/`, `apps/`, `games/`).
- **Core Framework (15 packages)**: **[emacs-taf/etaf](https://github.com/emacs-taf/etaf)** — `ecss`, `ekp`, `ebox`, `etaf`, `etaf-ui`, `etaf-posframe`, `etaf-ext`, `etaf-db`, `etaf-gamekit`, `etaf-install`, universal extensions and the bilingual reference manual.
- **Applications & Games**: Standalone product repositories below (`etaf-md`, `etaf-org`, `etaf-ncm`, `etaf-weread`, `etaf-xiangqi`, `etaf-tanks`, and more), automatically projected from the monorepo.

```elisp
;; Quick install in Emacs 29.1+ (no Git or C compiler required):
(require 'package)
(add-to-list 'package-archives '("etaf" . "https://etaf.top/packages/"))
(package-initialize) (package-refresh-contents)
(package-install 'etaf-install) (call-interactively #'etaf-install)
```

Browse the full catalog at [etaf.top](https://etaf.top) · Read [CONTRIBUTING.md](https://github.com/emacs-taf/.github/blob/main/CONTRIBUTING.md) · Licensed under [GPL-3.0-or-later](https://github.com/emacs-taf/emacs-taf/blob/main/LICENSE).
