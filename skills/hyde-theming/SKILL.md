---
name: hyde-theming
description: "Trigger: HyDE theme, wallbash, dcol, make theme, gallery, import. Guide HyDE theme creation, wallbash color system, and gallery management."
---

# HyDE Theming

## Making a Theme

Use the starter repo, rename theme in `justfile`:

```bash
git clone https://github.com/richen604/hyde-theme-starter ~/MyTheme
# Edit justfile: theme = "MyTheme"
just init
```

### Required structure

```
~/MyTheme/
├── Source/arcs/
│   ├── Gtk_<name>.tar.*       # GTK theme (mandatory)
│   ├── Icon_<name>.tar.*      # icon pack
│   ├── Cursor_<name>.tar.*    # cursor theme
│   └── Font_<name>.tar.*      # font
├── Config/.config/hyde/themes/MyTheme/wallpapers/
├── refs/                      # generated reference files
├── screenshots/
└── justfile
```

### Workflow

1. Copy wallpapers to theme's `wallpapers/`
2. `just install` — install theme
3. Set wallpaper (Super+Shift+W), toggle wallbash mode (Super+Shift+R)
4. `just gen-all && just set-wall` — generate theme files
5. `cp -r ./refs/* ./Config/.config/hyde/themes/MyTheme && just install`

### Theme files (.theme)

Header format: `file_path|command`. Key vars in `hypr.theme`: `$GTK_THEME`, `$ICON_THEME`, `$COLOR_SCHEME`, `$CURSOR_THEME`, `$CURSOR_SIZE`.

### Gallery submission

```bash
python3 generate_readme.py
git init && git add . && git commit -m "My theme"
git remote add origin <repo-url> && git push -u origin main
```
Fork [hyde-gallery](https://github.com/HyDE-Project/hyde-gallery), add to list and `hyde-themes.json`.

## Wallbash & dcol

4 primary color groups, each with: 1 text color + 9 accent colors (44 base + RGBA variants).

Prefixes: `dcol_pry[1-4]`, `dcol_txt[1-4]`, `dcol_[1-4]ax[1-9]`. Suffixes: `_rgba(factor)` or `_rgb`.

For templates: use `wallbash_` prefix + `< >` placeholders. E.g. `<wallbash_pry1>`.

Template directories in `~/.config/hyde/wallbash/`:
- `always/`: runs on theme + wallpaper + mode switch
- `theme/`: runs on theme + mode switch
- `scripts/`: custom scripts, access via `$WALLBASH_SCRIPTS`

## Gallery commands

```bash
hyde-shell theme.import --select        # import via fzf
hyde-shell theme.select                 # pick active theme
hyde-shell wallpaper -S                 # pick wallpaper
hyde-shell theme.import --fetch "Name"  # update theme
hydectl theme import --name "N" --url "U"
hydectl theme set "Theme Name"
```

## Fetching Documentation

When a user asks for detailed theming info, fetch the relevant page at `https://hydeproject.pages.dev<path>`:

- Full theme walkthrough, arcs, .theme files → `/en/theming/making-themes/`
- Wallbash color system, dcol templates → `/en/theming/wallbash-and-dcol/`
- Gallery theme list, wallpaper commands → `/en/theming/gallery/`
```
