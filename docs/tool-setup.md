# COSC 10001: Student Tool Setup

**Everything here is free. None of it requires a credit card.**

> ### ⏰ Start GitHub Student Pack verification on day one, before you leave the classroom.
> It is **not instant**: it can take several days. Almost everything else in this list waits on it.

---

## What you need, and in what order

| # | Thing | When | Why |
|---|---|---|---|
| 1 | GitHub account | **First week** | Everything else hangs off this |
| 2 | GitHub Student Developer Pack | **First week** | Unlocks Copilot and ~20 other tools |
| 3 | GitHub Copilot Student plan | First week | **Your primary coding agent** |
| 4 | **IntelliJ IDEA**, and the `karel-starter` project | **Before Wed, Sep 2** | The editor for this course. **It installs Java for you** |
| 5 | A terminal, Git, and Node.js | Before Wed, Sep 9 | Where the rest of the work happens |
| 6 | GitHub Copilot CLI | Before Wed, Sep 23 | Your agent, in the terminal |
| 7 | ChatGPT free account + Codex CLI | Before Wed, Sep 23 | Your **second** agent, for comparison |

> ### 🐢 Only rows 1 to 4 matter this week.
> Row 4 is a download bar and a few dialog boxes, and it is the whole of your homework for **Wed, Sep 2**. Rows 5 through 7 have their own weeks and their own pages, and nothing is gained by racing ahead to them.

All of it is free, and the [Schedule](schedule.md) has the dates.

---

## 1. GitHub account

Sign up at <https://github.com>.

**Choose your username carefully.** This is a professional identity you'll carry into job applications: `bwei` or `bingyangwei`, not `xX_c0d3lord_Xx`. Changing it later breaks every link anyone has to your work.

Use whichever email you'll keep after graduation as the primary, and **add your `@tcu.edu` address as a secondary**: verification needs it.

---

## 2. GitHub Student Developer Pack

Apply at <https://education.github.com/pack>. You'll need:

- Your `@tcu.edu` email, added and verified on your GitHub account
- Proof of enrollment: a dated class schedule from my.tcu.edu works well
- A real name and profile photo on the account, since sparse accounts get rejected more often

**If you get rejected**, it's usually the enrollment proof. Reapply with a clearer, dated document. Email me if you're rejected twice; I can verify your enrollment directly.

Besides Copilot, the Pack unlocks JetBrains IDEs, cloud credits, free domain names, and a couple dozen other tools. Worth browsing once it lands.

---

## 3. GitHub Copilot Student: your primary agent

Once the Pack is approved, the Copilot Student plan attaches to your account automatically: unlimited code completions, **200 AI credits per month** for chat and agent mode, automatic model selection, and Copilot CLI.

Two hundred credits is genuinely enough for this course; every assignment is sized to fit. But it's a **budget**, and working inside one is part of the job:

- **Completions don't cost credits.** Only chat and agent-mode requests do.
- **One well-specified request beats five vague ones.** "Add error handling" costs the same as "Add a try/except around the file read in `main.py` that prints a clear message when the file is missing", and only one of them works the first time.
- **Check your usage** in GitHub Settings → Copilot before the end of the month, not after.
- Credits reset monthly. Don't hoard them, and don't burn a month's worth on the first weekend.

**In this course you drive it from the terminal, with Copilot CLI.** Editor plugins exist for IntelliJ and for VS Code, but no assignment here needs one.

**Nothing to install yet.** Copilot CLI needs a terminal and Node.js, which are [step 5](#5-a-terminal-git-and-nodejs) and are due before **Wed, Sep 9**. Get the Pack approved now; install the agent later.

---

## 4. IntelliJ IDEA, and Karel

**This is your homework for Wed, Sep 2, and it is the only thing on the list.**

Download IntelliJ from **<https://www.jetbrains.com/idea/download/>**, then open the `karel-starter` project inside it. Both halves, step by step and with every dialog named, are on their own page: **[IntelliJ + Karel](setup-intellij.md)**.

> **You do not have to install Java yourself.** Java comes as something called a **JDK**, and putting one on a laptop by hand is the classic way a first week goes sideways: a JRE instead of a JDK, a wrong `PATH`, `javac` mysteriously silent. **IntelliJ downloads a JDK for you from a dialog box**, and the guide says exactly which one to pick. This is the main reason this course uses IntelliJ.

**It will not disturb Intro to Programming.** The JDK IntelliJ fetches lives in a folder of its own and is used by IntelliJ alone, so whatever Java that course has you install is untouched by it. If the two courses' instructions ever seem to disagree, **Intro to Programming wins**, and nothing on this page is asking you to change anything over there.

> **Yes, this is a different editor from your programming class, which uses VS Code. That's on purpose and it is not extra work.** Both drive the same `javac` underneath, you'll watch that happen on the projector, and being able to sit down in front of two editors instead of one is a small, real advantage. **IntelliJ is free**, and no assignment in this course needs a paid version of anything.

**What Karel is:** a robot in a grid who understands four commands: `move()`, `turnLeft()`, `pickBeeper()`, `putBeeper()`. That's the entire language. We use it because it's small enough to learn in ten minutes, and because when your program is wrong you *see* the robot walk into a wall instead of reading a stack trace.

**Read chapters 1–2 of [Stanford's Karel reader](https://compedu.stanford.edu/karel-reader/docs/java/en/chapter1.html)** as well. Free, short, and written for people who have never programmed.

**If it doesn't work, come to class with it broken.** That is genuinely the assignment: the session is built around fixing exactly this, and you'll understand *why* it broke in a way you wouldn't have if it had just worked. Bring the exact error message.

---

## 5. A terminal, Git, and Node.js

**Not this week.** This one is due before the **Git session on Wed, Sep 9**, and there's nothing to gain by doing it early.

Follow the guide for your machine, on your own time. We do not install anything in class: fifty minutes a week does not stretch to a room of people downloading the same files, and class time is for fixing what broke.

| Your machine | Guide |
|---|---|
| **Windows** | [WezTerm + PowerShell 7](setup-windows.md) |
| **macOS** | [Ghostty + zsh](setup-macos.md) |

Both guides end with a block that prints the version of every tool. If all of them print, you're done. **If any of them error, bring your laptop to class or office hours. Don't quietly stay broken.**

> **Optional, not graded:** MIT's [The Missing Semester](https://missing.csail.mit.edu/) is a short free course on the shell, Git, and debugging: the things every CS program assumes you know and never teaches. The first three lectures cover our first two sessions in more depth, at your own pace.

---

## 6. Copilot CLI: your agent in the terminal

Once the Pack is approved and you have a terminal from step 5, this is one line. Both terminal guides include it, and it needs to work by **Wed, Sep 23**.

```bash
npm install -g @github/copilot
```

Then run `copilot` inside a project folder and it walks you through signing in.

---

## 7. Codex CLI: your second agent

You'll run the **same task through two different tools and compare what comes back**. You can't see an agent's failure modes until you have something to compare it against.

1. Create a free account at <https://chatgpt.com>
2. Install and verify it (Node.js required, from step 5):

```bash
npm install -g @openai/codex
codex --version
```

3. Run `codex` inside a project folder.

**Free tier:** roughly **10 tasks per day** on a rolling window, with a weekly cap. That's deliberately enough for the comparison exercise and not enough to build a whole project on. Use Copilot for building, Codex for comparing.

---

## Optional: Claude Code

I demo **Claude Code** in class most weeks. You are not required to have it and no assignment needs it.

**Claude Builder Club** is the good route: Anthropic runs a campus program at <https://claude.com/programs/campus> with student-led chapters that run hackathons and host workshops. Chapters have reported providing members with Claude Pro access and monthly API credits, and the organizer role carries a stipend. **If you want to start or join a TCU chapter, talk to me or a peer mentor.** It costs nothing, it's a genuinely good leadership item for a first-year résumé, and it would bring speakers to campus for the whole department.

**Paying for it yourself:** Claude Pro is about $20/month. **Don't buy it for this course.** Nothing you're graded on requires it, and I'd rather you spent the money on a domain name for your Ship-It project. If you do have it: `npm install -g @anthropic-ai/claude-code`.

---

## Why we're not standardizing on one tool

This course requires *two* agents and demos a third. That's intentional: the skill that transfers is the **loop**, not the vendor.

> **prompt → plan → read the diff → verify → commit**

Copilot agent mode, Codex, and Claude Code all run that loop with different interfaces. In four years you'll be using something that doesn't exist yet, and what you'll carry into it is the loop and the judgment, not the keyboard shortcuts.

There's also an honest reason: institutional access to the premium tools costs roughly **$240 per student per year**. The department can't fund that, and I'm not going to build a course where students who can pay $20/month do better than students who can't. So the required stack is free, permanently, for all of you.

---

## Troubleshooting

**Student Pack rejected twice** → email me, I can verify enrollment directly.

**Pack approved but Copilot still shows Free** → sign out of GitHub completely and back in. It can take up to 24 hours to propagate; after that, check <https://github.com/settings/copilot>.

**`command not found` after installing something** → the tool installed fine, but your shell doesn't know where to look yet. Close the terminal completely and reopen it. This fixes it about 90% of the time.

**Out of Copilot credits mid-month** → tell me. Then fall back to Codex, which is on its own free tier, and to Copilot completions, which don't consume credits at all.

**Everything is broken and I don't know where to start** → bring the laptop to office hours. It's a normal thing to do and takes about ten minutes. Staying broken for three weeks is the thing that hurts you.

---

## First-week checklist

- [ ] GitHub account created, with a professional username
- [ ] `@tcu.edu` email added and verified on GitHub
- [ ] Student Developer Pack application **submitted**
- [ ] Joined the class Slack
- [ ] Day 1 survey completed

Those five are non-negotiable. Then, before **Wed, Sep 2**, three more and no others:

- [ ] **IntelliJ IDEA installed**, from <https://www.jetbrains.com/idea/download/>
- [ ] **`karel-starter` open in IntelliJ**: a JDK downloaded, no red underlines, and the green ▶ opening a window where Karel takes two steps. Walkthrough: [IntelliJ + Karel](setup-intellij.md)
- [ ] **Karel reader chapters 1–2** read

**That is the whole list. There is no terminal step this week**, and nothing here asks you to install Java by hand.

Then, before **Wed, Sep 9**:

- [ ] Terminal setup guide attempted: [Windows](setup-windows.md) or [macOS](setup-macos.md)

**Attempted, not necessarily working.** Coming to class with a broken install is the assignment. Coming with an untouched one is not.
