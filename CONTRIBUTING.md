# Contributing to Emacs TAF (ETAF)

Thank you for your interest in contributing to the Emacs TAF ecosystem!

## Monorepo First

All first-party ETAF framework packages, extensions, applications, games, the official installer and the reference manual are developed together in the **[Emacs TAF Monorepo](https://github.com/emacs-taf/emacs-taf)** under `packages/<package>/`.

Individual repositories (`https://github.com/emacs-taf/<package>`) are **read-only single-package projections** published from the monorepo so package managers (`straight.el`, `elpaca`) and browsers have a clean single-package history.

### Opening Issues

- You are welcome to open bug reports or feature requests either in the **[monorepo](https://github.com/emacs-taf/emacs-taf/issues)** or directly in the specific package repository you are using.
- Maintainers track issues across the whole organization, fix them in the monorepo, and reply with the commit link before closing.

### Opening Pull Requests

- **Recommended:** Clone the monorepo (`git clone https://github.com/emacs-taf/emacs-taf.git`), edit under `packages/<package>/`, and open your PR against `emacs-taf/emacs-taf`. That way full CI (`Repository structure` and cross-platform `Package installation`) runs automatically and GitHub marks your PR as **Merged**.
- If you already opened a PR on a single-package mirror, no need to panic or rewrite it — maintainers never merge directly on mirror repositories, but can import your patch into the monorepo with full author attribution and link the commit back to your PR.

## Local Checks

External contributors need only standard Git, Python 3.10+ and Emacs 29.1+:

```sh
git clone https://github.com/emacs-taf/emacs-taf.git
cd emacs-taf
make setup-hooks
make -C packages/<package> check
make structure-check
```

## Guidelines

- **Public API boundaries:** Every package declares its supported public API in its root `<pkg>.el` Commentary. Consumers must not require another package's internal `lisp/` modules.
- **Commit messages:** Follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) (title ≤ 72 characters plus a `Validation:` line). Check locally with `python3 scripts/check-commit-message.py <file>`.
- **Media policy:** Do not commit showcase screenshots or videos to Git (only compact ≤ 100 KB offline test inputs belong under `tests/fixtures/`). Showcase assets are hosted on <https://etaf.top/media/>.
