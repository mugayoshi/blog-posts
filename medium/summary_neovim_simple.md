# My Neovim Configuration for simple usage (not as IDE) 

This is a modular Neovim configuration that uses `lazy.nvim` for plugin management.
Personally, I use IDE for programming as of July 2025 because of LLM extensions.
However, Neovim is lighter than IDE so it's nice to have Neovim that looks nice and includes useful plugins for creating a simple file or searching a repository, etc..

Core Configuration (`vim-options.lua`):
- Sets standard indentation to 2 spaces.
- Remaps `<C-j>` to `<Esc>` in insert mode and disables the default escape key.
- Sets the leader key to the spacebar.
- Enables relative line numbers.
- Provides keymaps for Git commands (`<leader>gs`) and yanking the current file path (`<leader>yfp`).
- Enables spell checking for English.

Plugin Management (`init.lua`):
- It automatically installs `lazy.nvim` if it's not already present.
- It loads all plugin configurations from the `lua/plugins` directory.

Plugins:

Theme and Appearance:
- catppuccin: The "catppuccin-mocha" colorscheme is used, with custom highlighting for line numbers.
- lualine: A "dracula" themed statusline is configured.
- indent-blankline: Provides visual indentation guides.
- neo-tree: A file explorer that can be toggled with `<C-n>` and used to view buffers with `<leader>bf`.

Editing and Workflow:
- nvim-autopairs: Automatically closes pairs of brackets, parentheses, etc.
- telescope: Provides fuzzy finding for files (`<C-p>`), live grep (`<leader>fg`), and buffer switching (`<leader>fb`). It's configured with a dropdown theme.
- nvim-treesitter: For syntax highlighting and parsing. It's configured to automatically install and highlight a wide range of languages.

Git Integration:
- gitsigns: Adds git decorations to the sign column.
- vim-fugitive: A Git wrapper that allows you to run Git commands directly from Neovim.

My configuration is available at https://github.com/mugayoshi/dotfiles/tree/simple-neovim/.config
