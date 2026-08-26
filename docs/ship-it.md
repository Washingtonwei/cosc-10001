# The Ship-It Project

**COSC 10001 · 20% of your course grade** **Announced Wed, Sep 16 · Due Sun, Dec 6, 11:59 PM · Demo Day Wed, Dec 9**

---

## The assignment, in one sentence

**Build one small thing that actually works, publish it, and write an honest account of what your AI agent got wrong.**

The second half matters more than the first. Anyone can now generate code that runs. The skill that will still be worth something in four years is looking at fluent, confident output and saying *"no, that's wrong, and here's why."* That's what the biggest chunk of the rubric measures.

By winter break you'll have a working, public artifact with your name on it, built the way software is actually built in 2026: with an agent, by someone who checks its work. Most students don't build anything real until their second or third year, and by then a lot of them have quietly decided they're "not a builder."

---

## Scope: keep it small

> **A weekend of work. Not a semester.**

Every year, students in courses like this pick something enormous, panic for two days in November, and demo something broken. **A tiny thing that works and is well documented scores far higher here than an ambitious thing that doesn't run.** If you finish early and want to add more, go ahead. Start small anyway.

---

## Project menu

Pick one, or propose your own (email me by **Wed, Nov 4** for approval).

| Project | What it is | Good if you… |
|---|---|---|
| **Personal website** | A real page on the internet with your name on it, published via GitHub Pages | …want something you'll actually use on a résumé |
| **Discord bot** | Responds to a command in a server: a dice roller, a study timer, a meme fetcher | …are already in Discord all day |
| **Command-line tool** | Does one useful thing from the terminal: renames files, converts units, tracks habits | …liked the terminal session |
| **Data visualization** | Charts something you care about: your Spotify history, a sports stat, campus data | …like data and want to see it |
| **Browser extension** | Changes a website you use: blocks something, adds something, restyles something | …have a website that annoys you |
| **Text-based game** | Choose-your-own-adventure, quiz game, number game | …want something fun to demo |
| **Study tool** | Flashcard app, GPA calculator, schedule planner | …want to solve your own problem |

**Best rule for picking:** choose something you'd genuinely want to exist. You'll be looking at it for eleven weeks.

---

## What you turn in

Everything goes in **one public GitHub repository**. You can reuse the repo from Professional Foundations.

```text
your-project/
├── README.md          ← what it is, how to run it, one screenshot
├── AI-NOTES.md        ← the honest account (biggest single grade block)
└── [your actual code]
```

### 1. The working artifact

Someone else, following your README on a different computer, should be able to get it running.

### 2. `README.md`

```markdown
# Project Name

One sentence: what this does.

## What it does
A short paragraph. What problem does it solve, or what does it do for fun?

## Screenshot
![screenshot](screenshot.png)

## How to run it
Step-by-step. Assume the reader has never seen your project.

## What I'd add next
One or two things you'd build if you had another week.
```

### 3. `AI-NOTES.md`: the important one

This is where the learning gets assessed. **"It worked perfectly" is the worst possible answer**: it means either you didn't look closely, or you didn't build anything hard enough to matter.

```markdown
# AI Notes

## Tools I used
Which agent(s), and roughly how much of the code came from them.

## What it got right
What surprised you in a good way. Where did it save you real time?

## What it got wrong  ← the biggest section
At least **two specific failures**, in detail:

- **What I asked for:** ...
- **What it gave me:** ...
- **Why it was wrong:** ...
- **How I figured out it was wrong:** ...
- **How I fixed it:** ...

## What I had to understand myself
Where did you have to actually know something? Where did "just ask the agent
again" stop working?

## What I'd do differently
How would you prompt or work differently on the next project?
```

> **If you genuinely hit no failures**, your project was too simple. Go add a feature that breaks it. That's a legitimate and encouraged use of the last week.

### 4. The demo

**Science-fair format, not a podium.** Half the class demos at their tables for twenty minutes while the other half circulates, then you swap. You'll give it several times to groups of two or three, about two minutes each:

1. Show the thing working, 60 seconds
2. Tell them one thing the agent got wrong and how you caught it, 60 seconds

**You do not have to present to the whole room.** Everyone circulating is a first-year who built something too, and by the third time through you'll have it down. Bring your charger.

---

## Rubric: 100 points

| Category | Pts | What earns full marks |
|---|---|---|
| **It runs** | 30 | Works as described. Someone else could run it from your README |
| **README quality** | 20 | Clear, complete, has a screenshot, a stranger could follow it |
| **`AI-NOTES.md` depth** | **30** | **Two or more specific failures, honestly analyzed: what went wrong, how you caught it, how you fixed it** |
| **Demo** | 20 | Showed it working, explained one real failure, stayed near two minutes |

**The largest single block is for documenting what the AI got wrong.** A working project with a thin `AI-NOTES.md` scores in the 70s. A slightly rougher project with a sharp, specific failure analysis scores in the 90s. That is not a trick; it reflects what this course thinks is actually valuable.

---

## Timeline

| When | Do this |
|---|---|
| **Wed, Sep 16** | Project announced. Start thinking |
| **Wed, Sep 30** | Pick your project. Tell your pod what you chose |
| **Wed, Nov 4** | Deadline to propose a project not on the menu · pod check-in: everyone shows their repo, even if it's broken |
| **Wed, Nov 18** | Second pod check-in: **it should run by now**, even if it's ugly |
| **Sun, Dec 6** | **Everything due**: code, README, AI-NOTES pushed |
| **Wed, Dec 9** | Demo Day, the last class |

**Do not start this in November.** Eleven weeks is generous; two days is not. The students who enjoy this project are the ones who started a small version in September and improved it.

**Thanksgiving note:** you have a full week back on campus (Nov 30 – Dec 4) before the deadline, so office hours, your pod, and your mentor are all available for the final push. But break itself is a terrible time to *start*: campus is empty and nobody is around to unstick you. **Have something that runs before you leave.**

---

## Rules

**Allowed and encouraged:** using an agent for most or all of the code (that's the point), help from your pod, your peer mentor, or office hours, following tutorials, copying patterns from documentation, and rebuilding your own version of something that already exists.

**Not allowed:** submitting someone else's project, submitting a repository you didn't build this semester, or an `AI-NOTES.md` describing failures that didn't happen. **Fabricated failure analysis is an integrity violation**, same as fabricating an event reflection.

**AI zone: 🟢 Green.** Use whatever you want, however you want. `AI-NOTES.md` satisfies the AI Use Statement; you don't need a separate one.

---

## If you're stuck

**"I don't know what to build."** Pick the personal website. It's the most useful one long-term, it always works, and you'll use it in job applications.

**"My project is broken and it's November."** Come to office hours. A broken project three weeks out is completely normal and completely fixable. A broken project the night before is neither.

**"The agent keeps giving me code that doesn't work."** Excellent, write that down: that's `AI-NOTES.md` material. Then narrow your prompt: name the file, name the function, describe the exact behavior you want, and paste the actual error text.

**"I ran out of Copilot credits."** Tell me. Fall back on inline completions in VS Code, which don't consume credits, and on Codex. This is a logistics problem with a solution.

**"Mine is way less impressive than everyone else's."** Some of your classmates have been coding since they were twelve. The rubric doesn't measure ambition. It measures whether it works, whether you documented it, and whether you can explain what went wrong, and those are all available to you regardless of where you started.

---

## What a great submission looks like

A GPA calculator. About 80 lines of Python. It runs. The README has a screenshot, three clear steps, and a note that they'd add pass/fail courses next.

The `AI-NOTES.md` says: *the agent wrote a weighted-average function that looked completely correct and produced a plausible number, but it divided by the number of courses instead of by total credit hours, so a 1-credit course counted the same as a 4-credit one. I only caught it because I checked it against my actual transcript and got 3.4 instead of 3.6. Here's the line, here's the fix, and here's what I now do differently: I always test with numbers I already know the answer to.*

**That's an A.** Not because the project is impressive, but because that student learned the thing this course exists to teach.
