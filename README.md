# HyDE-Project Skills

Agent skills for [HyDE Project](https://github.com/HyDE-Project/HyDE) — a clean, aesthetic, modular development environment for Hyprland on Arch Linux.

[![skills.sh](https://skills.sh/b/PentSec/hyde-project-skills)](https://skills.sh/PentSec/hyde-project-skills)

## Installation

```bash
npx skills add PentSec/hyde-project-skills
```

Or install individual skills:

```bash
npx skills add PentSec/hyde-project-skills --skill hyde-install
npx skills add PentSec/hyde-project-skills --skill hyde-config
npx skills add PentSec/hyde-project-skills --skill hyde-shell
npx skills add PentSec/hyde-project-skills --skill hyde-theming
npx skills add PentSec/hyde-project-skills --skill hyde-troubleshoot
```

## Manual Installation

If `npx` is unavailable or you prefer a direct setup, clone and symlink:

```bash
git clone https://github.com/PentSec/hyde-project-skills.git
ln -s "$(pwd)/hyde-project-skills/skills/"* ~/.config/opencode/skills/
```

For other agents, replace the target path:

| Agent | Target path |
|-------|-------------|
| OpenCode | `~/.config/opencode/skills/` |
| Claude Code | `~/.claude/skills/` |
| Cursor | `~/.cursor/skills/` |
| Windsurf | `~/.codeium/windsurf/skills/` |
| Cline / Codex | `~/.agents/skills/` |


## Skills

| Skill | Trigger | What it covers |
|-------|---------|---------------|
| **hyde-install** | HyDE install, setup, update, restore | Arch installation, flags, NVIDIA handling, updates, PSV restore |
| **hyde-config** | HyDE config, config.toml, Hyprland, Waybar | config.toml sections, Hyprland tree (boilerplate/override/user), Waybar layouts & group shapes |
| **hyde-shell** | hyde-shell, python-env, waybar.py, theme.import.py | Shell wrapper, venv management (create/sync/install/rebuild), tool flags |
| **hyde-theming** | HyDE theme, wallbash, dcol, gallery | Theme creation with starter kit, wallbash color system (44 colors), dcol templates, gallery commands |
| **hyde-troubleshoot** | troubleshoot, fix, NVIDIA, secrets, portals | Secrets & portals stack, theme vs mode, known issues table, common fixes |

## Usage

Once installed, your AI agent will automatically use these skills when you ask questions like:

- _"Install HyDE on Arch"_
- _"Configure Waybar with a custom layout"_
- _"Use hyde-shell to import a theme"_
- _"Make a theme with wallbash"_
- _"Fix NVIDIA issues in HyDE"_

Each skill also fetches the latest documentation from [hydeproject.pages.dev](https://hydeproject.pages.dev) when detailed answers are needed.

## License

Apache-2.0
