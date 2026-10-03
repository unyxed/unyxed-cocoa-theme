# Unyxed Cocoa Themes

Rich, low-glare cocoa themes in four flavors, each with a dark and a light variant.

Every theme ships for **Zed**, **Windows Terminal** and **Obsidian** (via the AnuPpuccin theme),
all generated from one file: `palettes.json`.

| Family | Themes |
|---|---|
| Cocoa Rose | Cocoa Rose Dark, Cocoa Rose Light |
| Rosewood | Rosewood Dark, Rosewood Light |
| Mocha Berry | Mocha Berry Dark, Mocha Berry Light |
| Cocoa Copper | Cocoa Copper Dark, Cocoa Copper Light |

`preview/index.html` shows every theme side by side (open it in a browser) with C++, TypeScript and Luau samples.

## Syntax colors

Nine syntax hues, spread around the color wheel with matched lightness so tokens are easy to tell apart
but the theme stays calm: declaration keywords, control flow, imports and preprocessor, strings, functions,
numbers, types, properties and operators each get their own color. The build enforces a minimum CIELAB
difference (delta E 25) between them. It works in any language: grammars that emit only plain `keyword`
(for example Luau) simply show one keyword color.

## Install

**Zed** (once): command palette, `zed: install dev extension`, select this repo folder.
Pick a theme with Ctrl+K, Ctrl+T. To follow the system light/dark mode:

```json
"theme": { "mode": "system", "light": "<Light theme name>", "dark": "<Dark theme name>" }
```

**Windows Terminal and Obsidian** (PowerShell, from this folder):

```powershell
.\install.ps1 -Vault "D:\path\to\Vault"
```

- Windows Terminal: restart it, then Settings > Profiles > Defaults (or a profile) > Appearance > Color scheme.
- Obsidian: install the AnuPpuccin theme, then Settings > Appearance > CSS snippets, and enable **one**
  `unyxed-cocoa-theme-*.css` snippet. Leave AnuPpuccin's custom color fields in Style Settings empty, or they override the snippet.
  Any AnuPpuccin flavor works as the base; Mocha (dark) and Latte (light) are good defaults.

If PowerShell refuses to run the script: `powershell -ExecutionPolicy Bypass -File .\install.ps1 -Vault "..."`.

## Update after a change

```powershell
git pull
python tools/build.py
.\install.ps1 -Vault "D:\path\to\Vault"
```

Zed picks up the rebuilt files from the folder; if a change does not show, reinstall the dev extension.

## Maintaining

Agents (Claude Code, opencode, etc.) maintain this repo; see `AGENTS.md`. Short version:
edit `palettes.json`, run `python tools/build.py`, commit everything.
Requires Python 3.9+ (no packages).

## Before publishing to the Zed extension store

Set the real `repository` URL in `extension.toml`, add a LICENSE file and screenshots, bump `version`.
