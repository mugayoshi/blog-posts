# Mac Settings

- Set Caps Lock to Ctrl (Modifier Keys)
  - If you use an external keyboard, you should set it for both built-in and external.
- Turn on TrackPad > Tap to click
- Turn on Keyboard > Touch Bar shows “F1, F2, etc. Keys”
- Turn on Keyboard > Function Keys >“Use F1, F2, etc. keys are standard function keys”
- Turn off “Automatically adjust brightness”

- Switch input source shortcut → cmd + space
  - only if you need multiple input sources

# Browser
## Extensions
- 1Password
- CrxMouse
- Grammarly
- React Developer Tools
- GoLinks

# Slack
- Change the setting “When writing a message, press Enter to.. “ (Preferences > Advanced)
- App integrations
  - Google Calendar
  - Google Drive
  - GitHub
  - Jira, etc.

# Productivity Apps
- [ ] Be Focused (Pomodoro timer)
  - https://apps.apple.com/es/app/be-focused-pomodoro-timer/id973134470?l=en-GB&mt=12
- [ ] Maccy (clipboard manager)Maccy - macOS clipboard manager
  - https://maccy.app/
  - it’s possible to get it for free

- [ ] Rectangle (move and resize windows) Rectangle
  - https://rectangleapp.com/

- [ ] Grammarly
  - https://chrome.google.com/webstore/detail/grammarly-grammar-checker/kbfnbcaeplbcioakkpcpgfkobkghlhen
  - The desktop app also exists.

- [ ] Alfred
  - https://www.alfredapp.com/

# Setups for Engineers
It’s recommended to follow these steps **in order**.

1. Homebrew https://brew.sh/
   1. It’s installed along with Git
2. set up a shell (Mac’s default shell is zsh)
   1. create and edit ~/.zsh if necessary
3. IDE (VSCode in my case)
   1. If you need to set a Python interpreter, set */usr/local/bin/python3.11*
4. Docker desktop

### Optional tools

- terminal
  - https://www.warp.dev/
    - setup Neovim
    - install [Startship](https://starship.rs/), etc. for custom prompt
- DB viewer
  - Table Plus
    - https://tableplus.com/
  - DataGrip
    - https://www.jetbrains.com/datagrip/
  - Beaver



- Google 日本語入力

  - インストールする

  - Mac を再起動 (**インストールしたあとは再起動しないと設定画面に出てこない**)

  - Keyboard > Text Input > Input Source で Hiragana(Google) を選択

  - 設定を変更
    - General タブを以下の内容にする
      - Basics
        - Input mode: Romaji
        - Punctuation style: ", ."
        - Symbol style: "[] ／"
        - Input from ￥ or backslash key: "Backslash \\"
        - Space  input style: "Halfwidth"
        - Candidate selection shortcut: "1-9"
        - Input from numpad keys: "Halfwidth"
      - Advanced
        - Numbers, (){}[], ,., “ を Halfwidth にする
