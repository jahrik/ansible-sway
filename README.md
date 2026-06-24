# SWAY

[![CICD](https://github.com/jahrik/ansible-sway/actions/workflows/cicd.yml/badge.svg)](https://github.com/jahrik/ansible-sway/actions/workflows/cicd.yml)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-jahrik.sway-blue?logo=ansible)](https://galaxy.ansible.com/ui/standalone/roles/jahrik/sway/)

Installs [Sway](https://swaywm.org/) — an i3-compatible Wayland compositor ([GitHub](https://github.com/swaywm/sway)) — with waybar, dunst, and a full templated config to `~/.config/sway/`.

## OS Support

| Platform | Install method |
|---|---|
| Arch Linux | `pacman` (sway, dunst, seatd, waybar, wayland, wayland-protocols, xorg-xwayland); enables seatd service |
| Debian / Ubuntu | `apt` (sway, dunst, waybar) |

macOS and SteamOS are not supported — Sway is a Wayland compositor that requires kernel-level access.

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `install` | `true` | Set to `false` to uninstall Sway and remove `~/.config/sway` |
| `sway.lock` | `true` | Enable swaylock |
| `sway.bar` | `swayrbar` | Status bar: `polybar`, `waybar`, or `swayrbar` |
| `sway.terminal` | `alacritty` | Default terminal emulator |
| `sway.mod` | `Mod1` | Modifier key (Alt) |
| `sway.left` | `h` | Left direction key (vim-style) |
| `sway.down` | `j` | Down direction key |
| `sway.up` | `k` | Up direction key |
| `sway.right` | `l` | Right direction key |
| `sway.background` | `~/.config/sway/background.jpg` | Wallpaper path |

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - role: jahrik.sway
```

To uninstall:

```yaml
---
- hosts: all
  vars:
    install: false
  roles:
    - role: jahrik.sway
```

## Testing

```bash
uv sync
source .venv/bin/activate
yamllint .
ansible-lint
molecule test
```

Note: Sway cannot run inside Docker (no Wayland kernel capabilities). The verify step checks that the binary exists rather than launching the compositor.

## License

GPLv2

## Author Information

jahrik@gmail.com
