# Repository Guidelines

## Project Structure & Module Organization

This directory contains a private Doom Emacs configuration, not the Doom distribution itself.

- `init.el`: enables Doom modules and flags through `doom!`, including Corfu, Vertico, Evil, and language support.
- `packages.el`: declares additional dependencies with `package!`; currently adds `catppuccin-theme`.
- `config.el`: holds runtime preferences, including the Catppuccin Latte theme, line numbers, and `org-directory`.
- `readme.md`: documents setup, enabled features, and everyday configuration changes.

There are no separate source, test, or asset directories. Keep module selection, package declarations, and runtime settings in their respective files.

## Build, Test, and Development Commands

Run these commands using an existing Doom Emacs installation; this directory has no standalone build system.

- `doom sync`: synchronize packages and modules after changing `init.el` or `packages.el`, then restart Emacs.
- `doom doctor`: check the Doom environment for missing dependencies and configuration problems.
- `emacs`: launch the configured editor for interactive verification.

If `doom` is not on `PATH`, use the executable in your Doom installation's `bin/` directory. Changes limited to `config.el` do not require `doom sync`; restart Emacs to verify startup behavior.

## Coding Style & Naming Conventions

Preserve the lexical-binding file headers. Use standard Emacs Lisp indentation, spaces rather than tabs, and `M-x indent-region` to format edited forms. Follow existing alignment in the `doom!` module list and use descriptive, hyphenated Lisp names.

Wrap package-specific settings in `with-eval-after-load` when appropriate so package defaults do not override them. Keep variables that must be set before loading, such as `org-directory`, outside those blocks. No standalone formatter or lint configuration is present.

## Testing Guidelines

No automated test suite or coverage threshold is configured. Run `M-x check-parens` in edited Lisp files, restart Doom, and exercise the affected feature. For module or dependency changes, also run `doom sync` and `doom doctor`. Record validation steps and any remaining warnings.

## Commit & Pull Request Guidelines

The repository is initialized on `main` but has no commits yet, so no historical commit convention exists. Use concise, imperative subjects such as `Configure relative line numbers`. Keep changes focused, and update `readme.md` when setup or documented behavior changes. Pull requests should explain the behavior change, list validation performed, and link relevant issues. Include screenshots for visible theme or layout changes.
