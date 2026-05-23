---
name: hyde-shell
description: "Trigger: hyde-shell, python-env, waybar.py, theme.import.py, tool. Guide HyDE shell wrapper, venv, and tool scripts."
---

# HyDE Shell & Tools

## hyde-shell

Universal wrapper at `~/.local/bin/`. Auto-resolves scripts without extensions.

```bash
hyde-shell <command> [args]
hyde-shell --help | -h         # help
hyde-shell -r | reload          # reload env
hyde-shell waybar --set layout-1
hyde-shell theme.import --select
hyde-shell wallpaper -S
hyde-shell screenrecord
```

Built-in: `wallbash` (run wallbash scripts), `python-env` (venv management).

## python-env

Isolated venv at `$XDG_STATE_HOME/hyde/python_env` (default `~/.local/state/hyde/python_env`). Built on `uv`.

| Command | Effect |
|---------|--------|
| `create` | Create venv + install deps from pyproject.toml |
| `sync` | Sync deps after pulling updates |
| `install <pkg>` | Add package (persists across rebuild) |
| `uninstall <pkg>` | Remove package |
| `destroy` | Delete venv only (keeps pyproject.toml) |
| `rebuild` | Destroy + create + sync |
| `uv --hyde <args>` | Run uv scoped to HyDE venv |

Optional extras: `python-env uv --hyde sync --extra amd` (AMD GPU monitoring).

## waybar.py

```bash
waybar.py --select       # rofi layout picker
waybar.py --set <name>   # switch layout
waybar.py --next | --prev
waybar.py --watch        # persistent mode + auto-restart
waybar.py --kill         # kill all waybar processes
waybar.py --hide [0|1|toggle]
waybar.py --update       # full sync (icons, border-radius, includes)
waybar.py --update-icon-size | --update-border-radius | --generate-includes
```

## theme.import.py

```bash
theme.import.py --select        # fzf interactive picker
theme.import.py --fetch <name>  # update specific theme
theme.import.py --fetch all     # update all local themes
theme.import.py --json          # fetch gallery JSON
theme.import.py --skip-clone    # skip gallery repo clone
```

## Fetching Documentation

When a user asks for detailed flag docs, fetch the relevant page at `https://hydeproject.pages.dev<path>`:

- hyde-shell full man page → `/en/man-pages/hyde-shell/`
- python-env subcommands, extras → `/en/man-pages/python-env/`
- theme.import.py options → `/en/man-pages/themeimport/`
- waybar.py all flags → `/en/man-pages/waybarpy/`
```
