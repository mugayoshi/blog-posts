# Terminal Setup

1. create `.zshrc` and paste the setting to it.
  1. existing `.zshrc` is saved in [dotfiles](https://github.com/mugayoshi/dotfiles)


## Warp
Specific setting for Warp

1. download Hack Nerd Font fonts from [here](https://www.nerdfonts.com/font-downloads)

2. set Catppuchin theme
  1. create a custom theme directory
  ```
  mkdir -p $HOME/.warp/themes/
  ```
  2. copy and paste Catppuchin theme from https://github.com/catppuccin/warp
  3. restart Warp

  4. Custom prompt by [Starship](https://starship.rs/guide/)
        1. install Starship by Homebrew
      2. Set Gruvbox Rainbow Preset
      3. Edit the local `starship.toml`
                1. Copy `starship.toml` in `dotfies` repository and paste it to the local file.
      4. Open Warp Settings and select `PS1` for prompt (default is Warp prompt)
