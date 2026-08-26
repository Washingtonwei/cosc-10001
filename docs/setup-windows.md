# WezTerm + PowerShell 7 on Windows

A modern Windows terminal for Git, Copilot CLI, Codex, and Node.js. **No WSL**: your projects stay in normal Windows folders like `D:\Projects`.

> ### 📅 This is due before **Wed, Sep 9**, the Git session. Not before Wed, Sep 2.
> The Karel session needs nothing but IntelliJ, and [that guide](setup-intellij.md) is the whole of that week's homework. Doing this one early is fine; doing it *instead* is not.

```text
Windows
└── WezTerm
    └── PowerShell 7
        ├── Starship prompt
        ├── Git
        ├── Node.js
        ├── Copilot CLI
        ├── Codex CLI
        └── Claude Code (optional)
```

## 1. Install PowerShell 7

Windows ships an older "Windows PowerShell." Install the current one. In any terminal:

```powershell
winget install Microsoft.PowerShell
```

Close and reopen the terminal, then check that the major version is `7`:

```powershell
$PSVersionTable.PSVersion
```

The executable is `pwsh.exe`. You'll need that name in the next step.

## 2. Install WezTerm

```powershell
winget install wez.wezterm
```

WezTerm is a GPU-accelerated terminal with tabs, panes, custom fonts, and Lua configuration. Close and reopen your terminal after it installs.

## 3. Configure WezTerm

WezTerm reads `C:\Users\YourName\.wezterm.lua`. Open it:

```powershell
notepad $HOME\.wezterm.lua
```

Paste this in, changing `default_cwd` to your own project folder (forward slashes, even on Windows):

```lua
local wezterm = require("wezterm")
local config = wezterm.config_builder()

-- Open PowerShell 7 instead of WSL or Windows PowerShell
config.default_prog = { "pwsh.exe", "-NoLogo" }
config.default_cwd = "D:/Projects"

config.font = wezterm.font("JetBrains Mono")
config.font_size = 15
config.color_scheme = "Catppuccin Mocha"

config.window_background_opacity = 0.94
config.window_decorations = "TITLE | RESIZE"
config.window_padding = { left = 10, right = 10, top = 8, bottom = 8 }

config.enable_tab_bar = true
config.hide_tab_bar_if_only_one_tab = true
config.use_fancy_tab_bar = false

config.scrollback_lines = 100000
config.automatically_reload_config = true

config.keys = {
  { key = "c", mods = "CTRL|SHIFT", action = wezterm.action.CopyTo("Clipboard") },
  { key = "v", mods = "CTRL|SHIFT", action = wezterm.action.PasteFrom("Clipboard") },
  { key = "t", mods = "CTRL|SHIFT", action = wezterm.action.SpawnTab("CurrentPaneDomain") },
}

return config
```

Restart WezTerm and confirm it opened PowerShell 7, not WSL:

```powershell
$PSVersionTable.PSVersion
```

## 4. Install Starship

Starship gives you a prompt that shows your folder, your Git branch, and whether you have uncommitted changes, without you asking.

```powershell
winget install Starship.Starship
```

Then turn it on in your PowerShell profile:

```powershell
New-Item -ItemType File -Path $PROFILE -Force   # only if it doesn't exist yet
notepad $PROFILE
```

Add:

```powershell
Invoke-Expression (&starship init powershell)

Set-Alias ll Get-ChildItem
Set-Alias grep Select-String
```

Save and restart WezTerm. If PowerShell blocks the profile, run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` and restart again.

## 5. Install Git

```powershell
winget install Git.Git
```

Then set your identity. This gets attached to every commit you ever make, so use the same email as your GitHub account or your commits won't link to your profile:

```powershell
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
git config --global init.defaultBranch main
git config --global core.autocrlf true
```

## 6. Install Node.js

```powershell
winget install OpenJS.NodeJS.LTS
```

Restart WezTerm, then check `node --version` and `npm --version`.

## 7. Install the AI coding tools

**Copilot CLI (your primary agent).** Requires the GitHub Student Developer Pack: see [Tool Setup](tool-setup.md). Install it, then run `copilot` and it walks you through signing in.

```powershell
npm install -g @github/copilot
```

**Codex CLI (your comparison agent).**

```powershell
npm install -g @openai/codex
```

**Claude Code (optional).** Not required for anything in this course.

```powershell
npm install -g @anthropic-ai/claude-code
```

Both agents run inside a project folder:

```powershell
cd D:\Projects\MyProject
copilot
```

## 8. Useful PowerShell commands

| Command | What it does |
|---|---|
| `Get-ChildItem` (`ll`) | List files |
| `cd D:\Projects` | Change directory |
| `cd ..` | Go up one folder |
| `Get-Location` | Print the folder you're in |
| `mkdir MyProject` | Create a folder |
| `explorer .` | Open this folder in File Explorer |
| `idea .` | Open this folder in IntelliJ (if you ticked "Add bin folder to PATH") |
| `code .` | Open this folder in VS Code, for your programming class |
| `notepad README.md` | Open a file in Notepad |
| `Remove-Item file.txt` | Delete a file |
| `Remove-Item folder -Recurse` | Delete a folder and everything in it, **carefully** |
| Ctrl-C | Stop whatever is running |

## 9. Troubleshooting

**WezTerm opens WSL.** Delete any `config.default_domain = "WSL:Ubuntu"` and `config.wsl_domains` lines from `.wezterm.lua`, and make sure `config.default_prog = { "pwsh.exe", "-NoLogo" }` is present.

**WezTerm can't find `pwsh.exe`.** PowerShell 7 isn't installed. Go back to step 1.

**No minimize, maximize, or close buttons.** Your config says `window_decorations = "RESIZE"`, which hides the Windows title bar. Use `"TITLE | RESIZE"`.

**Starship doesn't appear.** Confirm `$PROFILE` contains the `Invoke-Expression` line, then reload with `. $PROFILE`.

**`copilot`, `codex`, or `claude` is not recognized.** Restart WezTerm first; that fixes it most of the time. If not, check that npm's global folder is on your PATH with `npm config get prefix`, and test with `Get-Command copilot`.

**Everything is broken.** Bring the laptop to office hours. Ten minutes in person beats three weeks of being stuck.

## 10. Final verification

Paste this whole block into WezTerm:

```powershell
$PSVersionTable.PSVersion
git --version
node --version
npm --version
starship --version
copilot --version
codex --version
```

Every line should print a version. If any line errors, that tool didn't install: go back to its section.

## Recommended stack

| Component | Recommendation |
|---|---|
| Terminal emulator | WezTerm |
| Shell | PowerShell 7 |
| Prompt | Starship |
| Font | JetBrains Mono |
| Git | Git for Windows |
| JavaScript runtime | Node.js LTS |
| AI coding tools | Copilot CLI and Codex CLI |
| Project location | Windows filesystem, not WSL |
| Editor | IntelliJ IDEA for this course; VS Code for Intro to Programming |
