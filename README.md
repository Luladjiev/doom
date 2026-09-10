# Doom Emacs Configuration

Personal Doom Emacs configuration maintained in `~/.config/doom`.

## Features

- Catppuccin Latte theme and absolute line numbers.
- Evil editing, Corfu completion with Orderless, and Vertico selection.
- Workspaces, snippets, folding, syntax checking, and Magit.
- Ghostel terminal emulator, powered by libghostty-vt.
- Language modules for Emacs Lisp, JavaScript with Tree-sitter, JSON, Markdown, Org, Python, shell, web, and YAML.
- macOS integration enabled conditionally on macOS.
- Org files configured to live in `~/org/`.

## Setup

An existing Emacs and Doom Emacs installation is required. This repository supplies the private configuration; it does not install Doom itself.

1. Place this checkout at `~/.config/doom`, preserving any existing configuration before replacing it. If using another location, set `DOOMDIR` to that directory when running Doom and Emacs.
2. From a terminal, synchronize the declared modules and packages:

   ```sh
   doom sync
   doom doctor
   ```

3. Address relevant dependency warnings, then launch or restart Emacs.

If `doom` is not on your `PATH`, invoke it from your Doom installation's `bin/` directory. The additional theme dependency, `catppuccin-theme`, is declared in `packages.el` and installed through `doom sync`.

## Configuration Files

| File | Purpose |
| --- | --- |
| `init.el` | Enable or disable Doom modules and their flags. |
| `packages.el` | Declare additional packages and package overrides. |
| `config.el` | Configure themes, editor behavior, and package settings. |
| [AGENTS.md](AGENTS.md) | Contributor workflow and coding guidelines. |

After editing `init.el` or `packages.el`, run `doom sync` and restart Emacs. Changes confined to `config.el` do not require synchronization; restart Emacs to verify them.

For example, set `display-line-numbers-type` to `'relative` in `config.el` to use relative line numbers. Adjust `org-directory` there to change where Org files are kept. Defer package-specific settings with `with-eval-after-load` when appropriate.

## Terminal

Run `M-x ghostel` to open a terminal. On first launch, accept the prompt to download
the native module for your platform. Supported macOS systems have prebuilt
binaries, so compiling with Zig is optional. Restart Emacs after enabling the
module and running `doom sync`.

## Validation

There is no automated test suite. Run `M-x check-parens` in edited Lisp files, restart Doom, and exercise the changed functionality. Run `doom doctor` after module or dependency changes and record relevant warnings when contributing.

Inside Doom, use `SPC h d h` (or `C-h d h`) to open its documentation and inspect module options before enabling additional flags.
