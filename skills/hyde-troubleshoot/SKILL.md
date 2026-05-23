---
name: hyde-troubleshoot
description: "Trigger: HyDE troubleshoot, fix, error, nvidia, secrets, portals, FAQ. Guide HyDE issue resolution, secrets/portals, and common problems."
---

# HyDE Troubleshooting

## Secrets & Portals

**Polkit auth**: `polkitkdeauth.sh` dispatches to hyprpolkitagent → polkit-gnome → polkit-kde fallbacks. Only one agent needed.

**Portal stack**: XDPH (Hyprland) primary → XDP-GTK fallback. Override at `~/.config/xdg-desktop-portal/hyprland-portals.conf`.

**UWSM session env**: scripts in `~/.config/uwsm/env.d/` (00-hyde.sh, 01-gpu.sh) and `~/.config/uwsm/env-hyprland.d/`. Do NOT edit unless you understand the cascade.

**Qt apps unstyled**: verify `echo $QT_QPA_PLATFORMTHEME` returns `qt6ct`. Install kvantum, qt5ct, qt6ct.

**Electron apps** (VSCode, Spotify, Discord): need app-specific wallbash templates in `~/.config/hyde/wallbash/scripts/`. Reliable path: Spicetify for Spotify, Vencord for Discord.

**Flatpak apps**: use bundled runtimes. Portal theming via XDP-GTK. Set up via `~/HyDE/Scripts/extra/install_fpk.sh`.

## Theme & Mode

- **Theme** (Super+Shift+T): full bundle (wallpaper, GTK, icons, cursor, colors)
- **Mode** (Super+Shift+R): cycle wallbash modes (auto/dark/light/theme)

Both call `theme.switch.sh` → `wallpaper.sh` → `color.set.sh` (dcol template engine).

**GTK4 plain white**: generate GTK4 via `just gen-gtk4` in theme dir, copy `refs/gtk-4.0/` to theme.

## Known Issues

| Problem | Fix |
|---------|-----|
| SDDM login loop (uppercase/special chars in username) | Edit `/usr/share/sddm/themes/[theme]/theme.conf`, set `AllowBadUsername=true` |
| No wallpaper thumbnails | Run `swwwallcache.sh` |
| Waybar blur unwanted | Comment `blurls = waybar` in each `~/.config/hypr/themes/*/theme.conf` |
| Rofi mouse breaks after waybar launch | Known Waybar issue; `sleep 0.1` workaround applied by default |
| Flatpak Qt apps ignore theme | Portal limitation; use system packages when possible |

## Common Fixes

- **Keyboard layout**: add to `~/.config/hypr/userprefs.conf` under `input { kb_layout = us,de }`, switch with Super+K
- **Remove pokemon** from shell: uninstall `pokego-bin`
- **Edit terminal intro**: `~/.config/zsh/user.zsh`
- **SDDM wallpaper**: run `~/.config/hypr/sddmwall.sh` on the desired wallpaper
- **Monitor resolution**: `~/.config/hypr/monitors.conf`, e.g. `monitor = DP-1,2560x1440@144,0x0,1`
- **Screen record**: use `wl-screenrec`, `wf-recorder`, `kooha`, or OBS
- **XWayland issues**: app must support Wayland; HyDE cannot fix this — use the discussion panel

## Fetching Documentation

When a user asks for in-depth troubleshooting, fetch the relevant page at `https://hydeproject.pages.dev<path>`:

- Secrets, portals, UWSM, theme internals → `/en/help/secrets/`
- FAQ, wallpaper, keyboard, SDDM, waybar → `/en/help/faq/`
- NVIDIA GPU→driver mapping → `/en/help/nvidia/`
- Restore PSV format, flags → `/en/resources/restore/`
