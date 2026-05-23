---
name: hyde-config
description: "Trigger: HyDE config, configure, config.toml, Hyprland, Waybar, layout. Guide HyDE config.toml, Hyprland tree, and Waybar customization."
---

# HyDE Configuration

## config.toml

Main config: `~/.local/share/hyde/schema/config.toml`. Use editor with schema validation. Key sections:

- `[hyprland]`: terminal, editor, browser, file manager, GTK theme, icon/cursor theme, font, color_scheme, bar, lockscreen, idle, cursor_size
- `[hyprland-start]`: startup daemons (bar, notifications, network, clipboard, wallpaper, polkit agent, idle, battery notify)
- `[wallpaper]`: backend (default swww), custom_paths list for global wallpapers
- `[wallbash]`: skip_template list
- `[waybar]`: font, icon_size, position (top/bottom), scale
- `[rofi.*]`: per-subcommand scale, font, style, args
- `[volume]`, `[brightness]`: steps, notify, boost_limit
- `[mediaplayer]`: format, max_length, prefix strings
- `[cava.*]`: channels (stereo/mono), range, bar chars, width per output target
- `[weather]`: location, temperature_unit, windspeed_unit, forecast_days
- `[battery.notify]`: thresholds (critical/low/full/unplug), interval, timer
- `[screenshot]`: annotation_tool (satty), OCR tesseract_languages
- `[wlogout]`: style

## Hyprland

Config tree at `~/.config/hypr/`:

1. **Boilerplate** (`~/.local/share/hyde/hyprland.conf`): do NOT edit
2. **Overrides**: use `config.toml` `[hyprland]` + `[hyprland-start]`
   - ⚠️ `~/.config/hypr/hyde.conf` is **deprecated** — do NOT use it
3. **User files** (persist across updates): `keybindings.conf`, `windowrules.conf`, `monitors.conf`, `userprefs.conf`

Hot-reload supported. Add keyboard layouts via `userprefs.conf` under `input { kb_layout = us,de }`, switch with Super+K.

## Waybar

Tree at `~/.config/waybar/`:
- `layouts/*.jsonc`: bar configs (select via `waybar.py --select` or `hyde-shell waybar -S`)
- `styles/*.css`: CSS per layout (auto-paired by basename)
- `modules/*.jsonc`: module configs (auto-included)
- `includes/`: auto-generated — do NOT edit manually
- `menus/`: GTK GObject XML files
- `user-style.css`: optional personal overrides

### Group shapes

pill-left, pill-right, pill-up, pill-down, pill-in, pill-out, leaf, leaf-inverse. Reuse with `#tag` suffix.

### Making a layout

Copy from `~/.local/share/waybar/layouts/`, edit groups and modules, apply via `waybar.py --set my_config`. NEVER edit `~/.local/share/waybar/` — files are overwritten on update.

## Fetching Documentation

When a user asks a specific configuration question, fetch the relevant page at `https://hydeproject.pages.dev<path>`:

- Full config.toml sections and defaults → `/en/configuring/config_toml/`
- Hyprland config tree, layers → `/en/configuring/hyprland/`
- Waybar layouts, group shapes, step-by-step → `/en/configuring/waybar/`
