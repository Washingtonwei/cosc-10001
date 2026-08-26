# Ghostty + zsh on macOS

The Mac companion to the [Windows setup guide](setup-windows.md): same environment, different install commands.

> ### 📅 This is due before **Wed, Sep 9**, the Git session. Not before Wed, Sep 2.
> The Karel session needs nothing but IntelliJ, and [that guide](setup-intellij.md) is the whole of that week's homework. Doing this one early is fine; doing it *instead* is not.

```text
macOS
└── Ghostty
    └── zsh
        ├── Homebrew
        ├── Starship prompt
        ├── Git
        ├── Node.js
        ├── Copilot CLI
        ├── Codex CLI
        └── Claude Code (optional)
```

> **Which terminal?** macOS ships with Terminal.app, which works but is dated. This guide uses **Ghostty**: fast, modern, simple config. If you'd rather use **iTerm2**, substitute `iterm2` for `ghostty` in step 2 and set the font and colors in Settings → Profiles instead of step 4.

---

## 1. Xcode Command Line Tools

Almost everything else depends on these. Open **Terminal** (⌘-Space, type "Terminal"):

```bash
xcode-select --install
```

Click **Install** and wait. It's a few GB and slow on campus wifi. If it says they're already installed, move on.

---

## 2. Homebrew

Homebrew is the package manager for macOS. It's how you install everything below.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

It asks for your Mac password. **You won't see anything as you type**: no dots, no asterisks. That's normal Unix behavior, not a frozen terminal.

### Apple Silicon: the step everyone misses

On an M-series Mac (anything from 2020 on), Homebrew installs to `/opt/homebrew`, which your shell doesn't know about yet. Homebrew prints two commands under "Next steps" at the end of the install. **Run them.** They look like this:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Then `brew --version` should print a version. If you get `command not found`, those lines didn't run.

---

## 3. Ghostty and a good font

```bash
brew install --cask ghostty
brew install --cask font-jetbrains-mono
```

Open Ghostty (⌘-Space → "Ghostty"). **Type everything from here on in Ghostty**, not the built-in Terminal.

---

## 4. Configure Ghostty

Create the config file and your projects folder:

```bash
mkdir -p ~/.config/ghostty ~/Projects
open -e ~/.config/ghostty/config
```

Paste this in:

```ini
font-family = JetBrains Mono
font-size = 15
theme = catppuccin-mocha

background-opacity = 0.95
window-padding-x = 10
window-padding-y = 8
scrollback-limit = 10000000

working-directory = ~/Projects
```

Save (⌘-S) and restart Ghostty.

---

## 5. Starship

Starship gives you a prompt that shows your folder, your Git branch, and whether you have uncommitted changes, without you asking.

```bash
brew install starship
```

Turn it on in `~/.zshrc`, the zsh config file:

```bash
open -e ~/.zshrc      # if it doesn't exist: touch ~/.zshrc && open -e ~/.zshrc
```

Add:

```bash
eval "$(starship init zsh)"

alias ll="ls -lah"
alias gs="git status"
alias ..="cd .."
```

Then `source ~/.zshrc`. Your prompt should change immediately.

---

## 6. Git

macOS includes an old Git. Install a current one:

```bash
brew install git
```

Set your identity. This gets attached to every commit you ever make, so use the same email as your GitHub account or your commits won't link to your profile:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
git config --global init.defaultBranch main
```

---

## 7. Node.js

```bash
brew install node
```

Check `node --version` and `npm --version`.

---

## 8. The AI coding tools

**Copilot CLI (your primary agent).** Requires the GitHub Student Developer Pack: see [Tool Setup](tool-setup.md). Install it, then run `copilot` and it walks you through signing in.

```bash
npm install -g @github/copilot
```

**Codex CLI (your comparison agent).**

```bash
npm install -g @openai/codex
```

**Claude Code (optional).** Not required for anything in this course.

```bash
npm install -g @anthropic-ai/claude-code
```

Both agents run inside a project folder:

```bash
cd ~/Projects/my-project
copilot
```

---

## 9. Useful terminal commands

| Command | What it does |
|---|---|
| `ls` / `ls -lah` | List files / list them with details, including hidden ones |
| `cd ~/Projects` | Change directory |
| `cd ..` | Go up one folder |
| `pwd` | Print the folder you're in |
| `mkdir my-project` | Create a folder |
| `open .` | Open this folder in Finder |
| `idea .` | Open this folder in IntelliJ |
| `code .` | Open this folder in VS Code, for your programming class |
| `open -e file.txt` | Open a file in TextEdit |
| `cat file.txt` | Print a file's contents |
| `rm file.txt` | Delete a file, **no trash, no undo** |
| `rm -r folder` | Delete a folder and everything in it, **be careful** |
| `clear` | Clear the screen |
| ⌃-C | Stop whatever is running |

> `~` is your home folder. `.` means "right here." `..` means "one folder up."
>
> If `code` isn't found: open VS Code, press ⌘-Shift-P, and run "Shell Command: Install 'code' command in PATH". IntelliJ has the same thing under **Tools → Create Command-line Launcher**. Neither is required; both are convenient.

---

## 10. Troubleshooting

**`command not found` right after installing something.** The tool installed fine; your shell has a stale list of where programs live. **Close Ghostty completely and reopen it.** If it persists, run `which node` and `echo $PATH`. If `which` finds nothing, the install didn't finish: run it again and read the output.

**`brew: command not found`.** The Apple Silicon PATH step in section 2 didn't run. Run it, then restart Ghostty.

**Starship prompt doesn't appear.** Confirm `~/.zshrc` contains `eval "$(starship init zsh)"`, then `source ~/.zshrc`.

**`npm install -g` fails with a permissions error.** Don't reach for `sudo`. Run `which node`: if it says `/usr/local/bin/node` on an Apple Silicon Mac, you have a second Node from a `.pkg` installer. Bring it to office hours rather than fighting it.

**"Ghostty cannot be opened because the developer cannot be verified."** Right-click the app → **Open** → **Open**. macOS only asks once.

**Everything is broken.** Bring the laptop to office hours. Ten minutes in person beats three weeks of being stuck.

---

## 11. Final verification

Paste this whole block into Ghostty:

```bash
echo "zsh:";        zsh --version
echo "Homebrew:";   brew --version
echo "Git:";        git --version
echo "Node:";       node --version
echo "npm:";        npm --version
echo "Starship:";   starship --version
echo "Copilot:";    copilot --version
echo "Codex:";      codex --version
```

Every line should print a version. If any line errors, that tool didn't install: go back to its section.

---

## Recommended stack

| Component | macOS | Windows equivalent |
|---|---|---|
| Terminal | Ghostty (or iTerm2) | WezTerm |
| Shell | zsh | PowerShell 7 |
| Package manager | Homebrew | winget |
| Prompt | Starship | Starship |
| Font | JetBrains Mono | JetBrains Mono |
| Version control | Git | Git for Windows |
| JS runtime | Node.js | Node.js LTS |
| AI tools | Copilot CLI, Codex CLI | Copilot CLI, Codex CLI |
| Editor | IntelliJ IDEA | IntelliJ IDEA |

Both setups do the same things with different names. If you switch machines later, only the install commands change.
