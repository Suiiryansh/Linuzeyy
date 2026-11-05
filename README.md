# dotfiles

My Arch Linux setup: **Neovim** (LazyVim-based, wallpaper-driven colors, built-in C++ build/run), **kitty** terminal, and a few shell and git basics.

## What's inside

| Path | What it is |
| --- | --- |
| `.config/nvim/` | Neovim config: LazyVim plugin specs, a custom dashboard, the `caelestia` colorscheme, and a plugin-free C++ setup in `init.lua` |
| `.config/kitty/` | kitty config: beam cursor, cursor trail, font and zoom keys, theme palettes included from separate files |
| `.bashrc` | Minimal bash config with colored `ls` and `grep` |
| `.gitconfig` | Git identity placeholder (edit before use) |
| `install.sh` | Symlinks everything into `$HOME`, backing up anything it replaces |

## Highlights

### Neovim
- **C++ out of the box:** `clangd` starts automatically when installed, with `gd` (definition), `K` (docs), `gr` (references), `<leader>rn` (rename) and `<leader>ca` (code action).
- **Build and run:** press `F5` (or run `:VibeRun`) to compile the current C++ file with `g++ -std=c++20 -Wall -Wextra -g` and run it in a terminal split.
- **Wallpaper colors:** the `caelestia` colorscheme reads `~/.local/state/caelestia/scheme.json`, and the Ryoku spec tints tokyonight from `~/.cache/ryoku/colors.json`. Both fall back to a built-in scheme when those files don't exist.
- **Custom dashboard:** an ASCII header and a trimmed key list on the snacks.nvim start screen.
- **Quality of life:** relative line numbers, global statusline, smooth scrolling, system clipboard, yank highlight. `<Space>` is the leader and `<leader>w` saves.

### kitty
- SpaceMono Nerd Font is set in `kitty.conf`, and `current-font.conf` (included after it) overrides it with JetBrainsMono Nerd Font at size 12.
- `current-theme.conf` and `matugen.conf` hold generated color palettes.
- Put personal overrides in `~/.config/kitty/user.conf`. It loads last and is git-ignored.

## Requirements

- Neovim 0.11 or newer and `git`
- `kitty`
- [JetBrainsMono Nerd Font](https://www.nerdfonts.com/) and SpaceMono Nerd Font
- For C++: `clang` (gives you `clangd`) and `gcc`

On Arch (SpaceMono Nerd Font is optional, since `current-font.conf` overrides it; get it from nerdfonts.com or search with `pacman -Ss nerd`):

```bash
sudo pacman -S neovim git kitty clang gcc ttf-jetbrains-mono-nerd
```

## Install

```bash
git clone https://github.com/<your-username>/dotfiles.git ~/dotfiles
cd ~/dotfiles
./install.sh
```

The script symlinks each config into `$HOME`. Existing files are renamed to `*.bak.<timestamp>`, so nothing is lost. Then open `nvim` once and let lazy.nvim install the plugins.

Before committing or using `.gitconfig`, replace the placeholder name and email with your own.

## Notes

- `init.lua` is a small standalone setup and doesn't load `lua/config/lazy.lua`. To switch to the full LazyVim setup, add `require("config.lazy")` to `init.lua`.
- `.zshrc` is not included.

## Credits

- [LazyVim](https://github.com/LazyVim/LazyVim) and [folke's plugins](https://github.com/folke)
- Caelestia colorscheme format
