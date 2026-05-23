---
name: hyde-install
description: "Trigger: HyDE install, setup, update, arch, restore. Guide Arch HyDE installation, NVIDIA handling, updates, and config restore."
---

# HyDE Installation & Maintenance

## Prerequisites

Minimal Arch Linux install. May work on Arch-based distros but will conflict with GTK/Qt theming, shell, SDDM, GRUB on existing DE/WM setups.

## Install

Clone and run installer — NEVER as root/sudo:

```bash
pacman -S --needed git base-devel
git clone --depth 1 https://github.com/HyDE-Project/HyDE ~/HyDE
cd ~/HyDE/Scripts
./install.sh
```

### Installer flags

| Flag | Effect |
|------|--------|
| `(none)` | Full Hyprland + configs |
| `pkg_user.lst` | Full + your extra packages |
| `-i pkg_user.lst` | Minimal (core only, no configs) |
| `-d` | Minimal + `--noconfirm` |
| `-r` | Restore configs only |
| `-s` | Start & enable system services |
| `-t` | Test/dry run |
| `-m` | Skip theme install |
| `-n` | Skip NVIDIA |
| `-irst` | Dry-run all |

Copy `pkg_extra.lst` to `pkg_user.lst` for all extras.

## NVIDIA

Install.sh auto-detects NVIDIA GPU and maps to driver variant: 340xx / 390xx / 470xx / nvidia-dkms. GRUB or systemd-boot config is modified to enable NVIDIA DRM. Skip with `-n`.

## Update

```bash
cd ~/HyDE/Scripts
git pull origin master
./install.sh -r
```

Configs listed in `Scripts/restore_cfg.psv` get overwritten. Backups saved to `~/.config/cfg_backups`.

## Restore

```bash
./restore_cfg.sh <path/to/file.psv> [path/to/hyde/clone]
```

PSV format: `flag|path|target|dependency`. Flags: P(preserve), S(sync), O(overwrite), B(backup).

## Fetching Documentation

When a user asks a detailed question, fetch the relevant page at `https://hydeproject.pages.dev<path>`:

- System requirements, overview → `/en/getting-started/introduction/`
- Full install guide, flags, manual install → `/en/getting-started/installation/`
- How to update, granular updates → `/en/getting-started/update/`
- NVIDIA GPU to driver mapping → `/en/help/nvidia/`
- PSV restore format, flags → `/en/resources/restore/`
