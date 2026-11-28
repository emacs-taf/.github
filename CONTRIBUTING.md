# Contributing to Emacs TAF (ETAF)

Thank you for your interest in contributing to the Emacs TAF ecosystem!

## Monorepo First

All first-party ETAF framework packages, extensions, the official installer, the reference manual, applications and games are developed together in the **[Emacs TAF Monorepo](https://github.com/emacs-taf/emacs-taf)**:

- `core/packages/` — 15 core framework, extension, installer and reference-manual packages (automatically projected together into **[emacs-taf/etaf](https://github.com/emacs-taf/etaf)**).
- `apps/` and `games/` — standalone end-user products (each published product automatically projects to its own `https://github.com/emacs-taf/<package>` repository).

### Pull Requests

- **All pull requests must be opened against [emacs-taf/emacs-taf](https://github.com/emacs-taf/emacs-taf/pulls).**
- Read-only projection repositories (`emacs-taf/etaf` and individual app/game mirrors) have Pull Requests disabled to prevent history divergence from the monorepo.
- Opening your PR in `emacs-taf/emacs-taf` automatically runs full structure/API checks, cross-platform installation tests and auto-labels your PR by layer and package.

### Issues

- **Core framework, extensions, installer, manual & tooling**: please open issues in **[emacs-taf/emacs-taf/issues](https://github.com/emacs-taf/emacs-taf/issues)** using the structured package selector form.
- **Standalone applications & games**: you are welcome to open issues either in the specific application repository (e.g. `emacs-taf/etaf-md`) or in `emacs-taf/emacs-taf`. Maintainers track issues across the whole organization, fix them in the monorepo, and reply with the commit link before closing.

## Local Checks

External contributors need only standard **Git**, **Python 3.10+** and **Emacs 29.1+**:

```sh
git clone https://github.com/emacs-taf/emacs-taf.git
cd emacs-taf
make setup-hooks
make structure-check
make -C core/packages/etaf check   # or apps/<app>, games/<game>
```

## Guidelines

- **Public API boundaries:** Every package declares its supported public API in its root `<pkg>.el` Commentary. Consumers must not require another package's internal `lisp/` modules.
- **Commit messages:** Follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) (title ≤ 72 characters plus a `Validation:` line). Verify locally with `python3 scripts/check-commit-message.py <file>`.
- **Media policy:** Do not commit showcase screenshots or videos to Git (only compact ≤ 100 KB offline test inputs belong under `tests/fixtures/`). Showcase assets are hosted on <https://etaf.top/media/>.
