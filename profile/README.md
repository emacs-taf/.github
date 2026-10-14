<h1 align="center"><img src="https://raw.githubusercontent.com/emacs-taf/etaf/main/design/etaf-logo.svg" alt="ETAF — Emacs Text Application Framework" width="480"></h1>

**ETAF** builds complete text applications in Emacs with a web-style model:
declarative components and reactive state, CSS cascade styling, Box/Flex/Grid
layout, and incremental buffer updates instead of full redraws. Around it sit a
shared UI catalog, data backends, and a growing set of applications — a music
player, readers, chat and video clients.

**Core packages**

| Package | Function |
| --- | --- |
| [ecss](https://github.com/emacs-taf/ecss) | CSS cascade engine: selectors, specificity and computed styles |
| [ekp](https://github.com/emacs-taf/ekp) | Knuth–Plass paragraph line breaking |
| [ebox](https://github.com/emacs-taf/ebox) | Box/Flex/Grid layout, rendering and incremental buffer updates |
| [etaf](https://github.com/emacs-taf/etaf) | Components, reactive state and the application runtime |
| [etaf-ui](https://github.com/emacs-taf/etaf-ui) | Reusable UI components: buttons, forms, panels and window shells |
| [etaf-db](https://github.com/emacs-taf/etaf-db) | Data backends for ETAF applications; SQLite today |

[emacs-taf](https://github.com/emacs-taf/emacs-taf) is the development
workspace: it records the repository map, integration checkpoints and the shared
engineering rules. Each package keeps its own public interface, checks and
releases; start from its README and root entry Commentary.

The documentation is published at <https://etaf.top>.
