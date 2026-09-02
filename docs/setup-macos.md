# Terminal Setup on macOS

The Mac companion to the [Windows setup guide](setup-windows.md): same environment, different install commands.

> ### 📅 This is due before **Wed, Sep 9**, the Git session. Not before Wed, Sep 2.
> The Karel session needs nothing but IntelliJ, and [that guide](setup-intellij.md) is the whole of that week's homework. Doing this one early is fine; doing it *instead* is not.

> ### ⏱️ The required part is about half an hour, most of it download bars.
> Everything after that is optional. It makes the terminal nicer to look at and live in, and none of it is needed for any assignment in this course. **Do the required part, then stop if you want to.** Come back to the rest when you're curious, over a weekend, when nothing is due.

```text
Terminal.app                  ← already on your machine
└── zsh                       ← already on your machine
    └── Homebrew              ← required, and it installs the rest
        ├── Git               ← required
        ├── Node.js           ← required
        ├── Copilot CLI       ← required
        ├── Codex CLI         ← required
        ├── Ghostty           ← optional
        ├── Starship prompt   ← optional
        └── Claude Code       ← optional
```

> **Why Homebrew?** On a Mac, almost everything you'll ever install from the command line comes through Homebrew. Learning `brew install <thing>` once means you already know how to install the next twenty things, and it keeps them all in one place where they can be updated together. Windows students are learning the same habit with `winget`. It's worth the twenty minutes.

---

## 1. Open your terminal

You already have one. Press **⌘-Space**, type `terminal`, and open **Terminal**. That's it. That's the whole step.

It runs **zsh**, which is fine. Every command in this course works in it: `javac`, `java`, `git`, `npm`, and both AI agents.

> **You'll see people online insist you need a "better" terminal.** You don't, not to learn anything, and definitely not this month. There's a section at the bottom if you want a nicer one later.

Try these, so the window feels less like a void:

```bash
pwd
ls
cd ~
```

---

## 2. Install Apple's Command Line Tools

Homebrew is built on top of these, so they come first. They're a few GB and slow on campus wifi, so start this before you need it.

```bash
xcode-select --install
```

Click **Install** and wait. If it says they're already installed, move on.

---

## 3. Install Homebrew

Homebrew is the package manager for macOS: one command that installs, updates, and removes command-line software. **Everything else on this page comes through it.**

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

It asks for your Mac password. **You won't see anything as you type**: no dots, no asterisks. That's normal Unix behavior, not a frozen terminal.

### ⚠️ Apple Silicon: the step everyone misses

**Read this one twice.** It is, every single year, the step that leaves people stuck.

On an M-series Mac (anything from 2020 on), Homebrew installs itself to `/opt/homebrew`, and your shell does not yet know that folder exists. Homebrew prints two commands under **"Next steps"** at the end of the install. **Run them.** They look like this:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Now prove it worked before you go any further:

```bash
brew --version
```

**If that prints a version, you're fine.** If it says `command not found`, those two lines didn't run. Scroll up in your terminal, find the "Next steps" block Homebrew printed, and run what it says. Don't continue until `brew --version` answers, because every step below depends on it.

---

## 4. Install Git

Git is how your code gets a history and gets to GitHub. We use it in class on Wed, Sep 9.

```bash
brew install git
```

Then set your identity. This gets attached to every commit you ever make, so use **the same email as your GitHub account** or your commits won't link to your profile:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
git config --global init.defaultBranch main
```

> macOS already had a Git, an older one, bundled with the Command Line Tools. Homebrew's is current and is the one your shell will now find first. Having both is normal and nothing to fix.

---

## 5. Install Node.js

You are not going to write any JavaScript in this course. Node is here for one reason: it's how both AI agents install.

```bash
brew install node
```

**Close Terminal and reopen it**, then check:

```bash
node --version
npm --version
```

---

## 6. Install the AI coding tools

**Copilot CLI**, your primary agent. It needs the GitHub Student Developer Pack approved first: see [Accounts & Tools](tool-setup.md#2-github-student-developer-pack).

```bash
npm install -g @github/copilot
```

Run `copilot` once and it walks you through signing in.

**Codex CLI**, your comparison agent. We run the two side by side on Wed, Sep 23 and the differences are the point.

```bash
npm install -g @openai/codex
```

Both agents run *inside* a project folder, not in the abstract:

```bash
cd ~/Projects/my-project
copilot
```

---

## 7. Check it all worked

Close Terminal, open a fresh one, and paste this whole block in:

```bash
brew --version
git --version
node --version
npm --version
copilot --version
codex --version
```

**Six lines, six version numbers.** If one errors, that tool didn't install: go back to its section. If a tool you just installed says `command not found`, close the window and open a new one before you believe it.

That's the assignment. **If you got six versions, you're done and you can stop here.**

---

## Optional: make the terminal nicer

None of this is required. Nothing in this course grades it, and no assignment breaks without it. It's here because a terminal you like looking at is one you'll actually open, and because at some point you'll want to know what those people online were on about.

**Do this on a weekend, not the night before class.**

### Ghostty and a good font

macOS Terminal works but is dated. Ghostty is fast, modern, and simple to configure.

```bash
brew install --cask ghostty
brew install --cask font-jetbrains-mono
```

Open Ghostty (⌘-Space → "Ghostty"). If you'd rather use **iTerm2**, substitute `iterm2` above and set the font and colors in Settings → Profiles instead of the config file below.

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

### Starship

A prompt that shows your folder, your Git branch, and whether you have uncommitted changes, without you asking.

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

### Claude Code

Not required for anything in this course. The instructor demos it in class.

```bash
npm install -g @anthropic-ai/claude-code
```

---

## Useful terminal commands

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
> `ll` and `gs` come from the optional Starship section above. If you skipped it, type the long versions.
>
> If `code` isn't found: open VS Code, press ⌘-Shift-P, and run "Shell Command: Install 'code' command in PATH". IntelliJ has the same thing under **Tools → Create Command-line Launcher**. Neither is required; both are convenient.

---

## Troubleshooting

**`command not found` right after installing something.** The tool installed fine; your shell has a stale list of where programs live. **Close Terminal completely and reopen it.** If it persists, run `which node` and `echo $PATH`. If `which` finds nothing, the install didn't finish: run it again and read the output.

**`brew: command not found`.** The Apple Silicon PATH step in section 3 didn't run. Go back and run it. This is the most common failure on this page by a wide margin.

**`git` asks to install the Command Line Tools.** That's step 2 and it hasn't run yet. Let it.

**`npm install -g` fails with a permissions error.** Don't reach for `sudo`. Run `which node`: if it points somewhere unexpected, you may have two copies of Node from two different installers. Bring it to office hours rather than fighting it.

**Everything is broken.** Bring the laptop to office hours. Ten minutes in person beats three weeks of being stuck.

The rest of these only apply if you did the optional section:

**Starship prompt doesn't appear.** Confirm `~/.zshrc` contains `eval "$(starship init zsh)"`, then `source ~/.zshrc`.

**"Ghostty cannot be opened because the developer cannot be verified."** Right-click the app → **Open** → **Open**. macOS only asks once.

---

## Recommended stack

| Component | macOS | Windows equivalent | Needed for this course? |
|---|---|---|---|
| Terminal | Terminal.app | Windows Terminal | ✅ Required, already installed |
| Shell | zsh | PowerShell | ✅ Required, already installed |
| Build prerequisites | Xcode Command Line Tools | (already in Windows) | ✅ Required |
| Package manager | Homebrew | winget | ✅ Required |
| Version control | Git (via Homebrew) | Git for Windows | ✅ Required |
| JS runtime | Node.js LTS | Node.js LTS | ✅ Required |
| AI tools | Copilot CLI, Codex CLI | Copilot CLI, Codex CLI | ✅ Required |
| Editor | IntelliJ IDEA | IntelliJ IDEA | ✅ Required |
| Terminal upgrade | Ghostty (or iTerm2) | WezTerm | ⚪ Optional |
| Prompt | Starship | Starship | ⚪ Optional |
| Font | JetBrains Mono | JetBrains Mono | ⚪ Optional |
| Third agent | Claude Code | Claude Code | ⚪ Optional |

Both setups do the same things with different names. If you switch machines later, only the install commands change.
