# AGENTS.md

This file provides guidance to AI coding agents when working with code in this repository.

## Role Overview

Installs and configures [Sway](https://swaywm.org/), a tiling Wayland compositor (i3-compatible). Supports Arch Linux (via pacman + seatd) and Debian/Ubuntu. Deploys `~/.config/sway/config` from a Jinja2 template.

## Key Variables

| Variable | Default | Description |
|---|---|---|
| `install` | `true` | Set to `false` to uninstall sway and remove config |
| `sway.lock` | `true` | Enable swaylock |
| `sway.bar` | `swayrbar` | Status bar: `polybar`, `waybar`, or `swayrbar` |
| `sway.terminal` | `alacritty` | Default terminal emulator |
| `sway.mod` | `Mod1` | Modifier key (Alt) |
| `sway.left/down/up/right` | `h/j/k/l` | Vim-style direction keys |
| `sway.background` | `~/.config/sway/background.jpg` | Wallpaper path |

## Task Flow

- `tasks/main.yml` — branches install/uninstall on `install` var
- `tasks/install.yml` — includes OS-specific tasks, creates config dir, templates config, copies background
- `tasks/archlinux.yml` — installs sway + extras via `community.general.pacman`; enables seatd service
- `tasks/debian.yml` — installs sway via `apt`; installs dunst + waybar
- `tasks/uninstall.yml` — removes package and `~/.config/sway`

## Testing

```bash
uv sync
source .venv/bin/activate
yamllint .
ansible-lint
molecule test
molecule converge
molecule destroy
```

## CI

- **Lint**: yamllint + ansible-lint
- **Molecule**: Ubuntu 24.04 + Arch Linux via Docker (verify checks binary only — Wayland needs kernel access)
- **Release**: publishes to Ansible Galaxy on merge to `main`
