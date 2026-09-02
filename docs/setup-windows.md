# Terminal Setup on Windows

Git, Node.js, and your AI coding tools, in a terminal you already have. **No WSL**: your projects stay in normal Windows folders like `D:\Projects`.

> ### 📅 This is due before **Wed, Sep 9**, the Git session. Not before Wed, Sep 2.
> The Karel session needs nothing but IntelliJ, and [that guide](setup-intellij.md) is the whole of that week's homework. Doing this one early is fine; doing it *instead* is not.

> ### ⏱️ The required part is four installs and about fifteen minutes.
> Everything after that is optional. It makes the terminal nicer to look at and live in, and none of it is needed for any assignment in this course. **Do the required part, then stop if you want to.** Come back to the rest when you're curious, over a weekend, when nothing is due.

```text
Windows Terminal          ← already on your machine
└── PowerShell            ← already on your machine
    ├── Git               ← required
    ├── Node.js           ← required
    ├── Copilot CLI       ← required
    ├── Codex CLI         ← required
    ├── PowerShell 7      ← optional
    ├── WezTerm           ← optional
    ├── Starship prompt   ← optional
    └── Claude Code       ← optional
```

---

## 1. Open your terminal

You already have one. Press the **Windows key**, type `terminal`, and open **Windows Terminal**. That's it. That's the whole step.

It opens **Windows PowerShell**, which is fine. Every command in this course works in it: `javac`, `java`, `git`, `npm`, and both AI agents.

> **You'll see people online insist you need a "better" terminal.** You don't, not to learn anything, and definitely not this month. There's a section at the bottom if you want a nicer one later.

Try these, so the window feels less like a void:

```powershell
Get-Location
Get-ChildItem
cd ~
```

---

## 2. Install Git

Git is how your code gets a history and gets to GitHub. We use it in class on Wed, Sep 9.

```powershell
winget install Git.Git
```

**Close Windows Terminal and reopen it.** New installs don't show up in a window that was already open, which is the single most common "it didn't work" of this whole page.

Then set your identity. This gets attached to every commit you ever make, so use **the same email as your GitHub account** or your commits won't link to your profile:

```powershell
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
git config --global init.defaultBranch main
git config --global core.autocrlf true
```

---

## 3. Install Node.js

You are not going to write any JavaScript in this course. Node is here for one reason: it's how both AI agents install.

```powershell
winget install OpenJS.NodeJS.LTS
```

Close and reopen the terminal again, then check:

```powershell
node --version
npm --version
```

---

## 4. Install the AI coding tools

**Copilot CLI**, your primary agent. It needs the GitHub Student Developer Pack approved first: see [Accounts & Tools](tool-setup.md#2-github-student-developer-pack).

```powershell
npm install -g @github/copilot
```

Run `copilot` once and it walks you through signing in.

**Codex CLI**, your comparison agent. We run the two side by side on Wed, Sep 23 and the differences are the point.

```powershell
npm install -g @openai/codex
```

Both agents run *inside* a project folder, not in the abstract:

```powershell
cd D:\Projects\MyProject
copilot
```

---

## 5. Check it all worked

Close the terminal, open a fresh one, and paste this whole block in:

```powershell
git --version
node --version
npm --version
copilot --version
codex --version
```

**Five lines, five version numbers.** If one errors, that tool didn't install: go back to its section. If a tool you just installed says it isn't recognized, close the window and open a new one before you believe it.

That's the assignment. **If you got five versions, you're done and you can stop here.**

---

## Optional: make the terminal nicer

None of this is required. Nothing in this course grades it, and no assignment breaks without it. It's here because a terminal you like looking at is one you'll actually open, and because at some point you'll want to know what those people online were on about.

**Do this on a weekend, not the night before class.**

### PowerShell 7

Windows ships PowerShell 5.1. Version 7 is faster, handles errors better, and is the one most tutorials assume.

```powershell
winget install Microsoft.PowerShell
```

The executable is `pwsh.exe`, not `powershell.exe`. In Windows Terminal, click the **∨** next to the plus tab and pick **PowerShell** (the one without "Windows" in front). To make it the default: **Settings → Startup → Default profile**.

```powershell
$PSVersionTable.PSVersion    # major version should be 7
```

### WezTerm

A GPU-accelerated terminal with tabs, panes, custom fonts, and Lua configuration.

```powershell
winget install wez.wezterm
```

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

That config names **JetBrains Mono**, so install it too or WezTerm falls back to something plainer:

```powershell
winget install --id DEVCOM.JetBrainsMonoNerdFont
```

### Starship

A prompt that shows your folder, your Git branch, and whether you have uncommitted changes, without you asking.

```powershell
winget install Starship.Starship
```

Turn it on in your PowerShell profile:

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

Save and restart the terminal. If PowerShell blocks the profile, run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` and restart again.

### Claude Code

Not required for anything in this course. The instructor demos it in class.

```powershell
npm install -g @anthropic-ai/claude-code
```

---

## Useful PowerShell commands

| Command | What it does |
|---|---|
| `Get-ChildItem` | List files |
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

> `.` means "right here." `..` means "one folder up." `~` is your home folder.
>
> `ll` as a shortcut for `Get-ChildItem` comes from the optional Starship section above. If you skipped it, type the long name.

---

## Troubleshooting

**`git`, `node`, `copilot`, or `codex` "is not recognized."** Close the terminal window completely and open a new one. This fixes it most of the time, because a window that was already open has a stale list of where programs live. If it persists after a restart, check npm's global folder with `npm config get prefix`, and test with `Get-Command copilot`.

**`winget` isn't recognized.** You're on an older Windows build. Install **App Installer** from the Microsoft Store, or bring the laptop to office hours.

**Everything is broken.** Bring the laptop to office hours. Ten minutes in person beats three weeks of being stuck.

The rest of these only apply if you did the optional section:

**WezTerm opens WSL.** Delete any `config.default_domain = "WSL:Ubuntu"` and `config.wsl_domains` lines from `.wezterm.lua`, and make sure `config.default_prog = { "pwsh.exe", "-NoLogo" }` is present.

**WezTerm can't find `pwsh.exe`.** PowerShell 7 isn't installed. Install it first.

**No minimize, maximize, or close buttons.** Your config says `window_decorations = "RESIZE"`, which hides the Windows title bar. Use `"TITLE | RESIZE"`.

**Starship doesn't appear.** Confirm `$PROFILE` contains the `Invoke-Expression` line, then reload with `. $PROFILE`.

---

## Recommended stack

| Component | Recommendation | Needed for this course? |
|---|---|---|
| Terminal emulator | Windows Terminal | ✅ Required, already installed |
| Shell | Windows PowerShell | ✅ Required, already installed |
| Git | Git for Windows | ✅ Required |
| JavaScript runtime | Node.js LTS | ✅ Required |
| AI coding tools | Copilot CLI and Codex CLI | ✅ Required |
| Project location | Windows filesystem, not WSL | ✅ Required |
| Editor | IntelliJ IDEA for this course; VS Code for Intro to Programming | ✅ Required |
| Shell upgrade | PowerShell 7 | ⚪ Optional |
| Terminal upgrade | WezTerm | ⚪ Optional |
| Prompt | Starship | ⚪ Optional |
| Font | JetBrains Mono | ⚪ Optional |
| Third agent | Claude Code | ⚪ Optional |

The macOS version of this page is [here](setup-macos.md). Both setups do the same things with different names.
