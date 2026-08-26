# COSC 10001: Artificial Intelligence Policy

**Fall 2026 · Bingyang Wei**

---

## The short version

**You are expected to use AI tools in this course.** Understanding how they're reshaping software development is one of the six learning outcomes. Three rules:

1. **Disclose it.** Every submission ends with an AI Use Statement.
2. **You own it.** The agent's mistakes become your mistakes the moment you submit.
3. **Respect the Red zones.** A few things are deliberately AI-free.

That's the whole policy. The rest of this page explains why, and gives you the templates.

---

## Why this course is different

Most syllabi you get this semester will treat AI as a threat to be contained. This one doesn't. You're entering a field that changed underneath itself in about three years, and the people hiring you in 2030 will assume you can direct an AI agent the way your professors assume you can use a search engine.

But there is a real hazard, and it isn't the one people usually name. The hazard isn't that you'll cheat. It's that **you'll get a working result without ever understanding it**, repeatedly, for four years, and graduate unable to tell good output from confident garbage. Everything below is designed against that specific failure.

---

## Rule 1: Disclose

Every submission ends with an **AI Use Statement**. Two to three sentences. It is not a confession and it does not lower your grade. Omitting it does.

```markdown
## AI Use Statement

**Tool(s):** [e.g. GitHub Copilot agent mode, Codex CLI, Claude, none]
**What I asked it to do:** [one sentence]
**What I changed or rejected:** [one sentence]
**What I verified myself:** [one sentence]
```

### Examples

> **Tool(s):** GitHub Copilot agent mode. **What I asked it to do:** Scaffold a Python script to chart my top Spotify artists from a CSV. **What I changed or rejected:** It used a plotting library that isn't installed by default; I switched to matplotlib. **What I verified myself:** I hand-counted the top three artists from the raw CSV. The chart was off by one because the agent skipped the header row.

> **Tool(s):** Claude, for feedback only. **What I asked it to do:** I wrote the full draft myself, then asked it to point out paragraphs where my argument was unclear. **What I changed or rejected:** I rewrote my second paragraph based on its feedback and ignored its suggestion to add a conclusion, because I disagreed. **What I verified myself:** All the words submitted are mine.

> **Tool(s):** None. I wrote this reflection unaided, as required.

**"None" is a great answer.** Some of the best work in this course will have it.

---

## Rule 2: You own what you submit

If your agent invents a library that doesn't exist, cites a paper that was never written, misstates a fact about TCU's curriculum, or writes code that silently corrupts your data, **that is your error**, and it is graded as your error.

> ### "The AI said so" is not a defense.
> Not in this course, and not in the job you'll have in four years. The engineer who ships the bug owns the bug. This is the single most important professional habit this course can give you.

**Practical consequence:** before you submit anything an agent touched, you must be able to answer *"why is this line here?"* about every line. If you can't, you're not done; you're just holding something that hasn't broken yet.

| Type of output | How to verify |
|---|---|
| Code | Run it. Then run it on input it should fail on |
| A factual claim | Find it in a source that isn't the agent |
| A citation or link | Open it. Hallucinated citations look completely real |
| A library or API call | Confirm it exists in the actual documentation |
| A number | Recompute one case by hand |

---

## Rule 3: Green, Yellow, Red

Every assignment carries a color.

### 🟢 Green: use AI freely

Use whatever you want, however you want. Still disclose.

- **Ship-It project**, where the whole point is to use an agent
- **Both Build Checkpoints**
- Résumé drafting, studying, debugging your setup, preparing questions for a mentor or guest

### 🟡 Yellow: assistance yes, authorship no

You may use AI for structure, feedback, and proofreading. **The ideas and the sentences must be yours.** Do not ask it to write a draft and then edit the draft.

- CS Engagement event reflections
- The Peer Mentor Meeting reflection
- The Four-Year CS Development Plan

A good test: if you deleted every AI interaction and had to reproduce the submission from memory, could you? If no, you've crossed into Red territory.

### 🔴 Red: no AI at all

**In-class writing**, meaning anything you draft in the room: pod activities, questions you write down for a guest speaker, notes you take while an agent is failing on the projector in front of you. No laptop lid open to an agent while you are supposed to be thinking.

This isn't because AI would do it badly. It's because you need to know what your own unaided thinking feels like, and you can't know that if you never do it.

---

## Assignment-by-assignment

| Assignment | Zone | Notes |
|---|---|---|
| In-class writing | 🔴 Red | Written in the room, unaided |
| **Build Checkpoint 1: Karel** | 🟢 **Green** | Required. `NOTES.md` records what the agent got wrong |
| **Build Checkpoint 2: read a codebase** | 🟢 **Green** | Required. Explaining unfamiliar code is what agents are best at; the five bullets still have to be in your words |
| CS Engagement reflections | 🟡 Yellow | The required specifics can't be faked anyway |
| Peer Mentor reflection | 🟡 Yellow | n/a |
| Professional Foundations: résumé | 🟢 Green | Drafting with AI is industry-standard |
| Professional Foundations: profile README | 🟢 Green | n/a |
| **Ship-It project** | 🟢 **Green** | Required. `AI-NOTES.md` documents the collaboration |
| Four-Year CS Development Plan | 🟡 Yellow | It's your life; the thinking should be too |
| *This Week in CS* slide | 🟢 Green | Verify the story is real against the primary source before presenting it |

---

## What actually counts as a violation

**Not violations**, all fine and encouraged: using an agent to write most of your Ship-It code, asking AI to explain something you didn't understand in class, having it find the flaw in your argument, using it to fix your résumé formatting at 2 AM.

**Violations:**

- Submitting AI-generated work **without an AI Use Statement**
- Submitting AI-written prose in a 🔴 Red zone
- Fabricating an event reflection for an event you didn't attend, with or without AI
- Submitting a claim, citation, or number you never verified, when it turns out to be invented

Suspected violations go to the Dean's Office of the College of Science & Engineering under the TCU Student Code of Conduct.

---

## On cost and fairness

**No assignment in this course requires a paid AI subscription.** Every tool we use has a free tier sufficient for everything you're graded on, and assignments are sized to fit it. See [Tool Setup](tool-setup.md) for the free-access routes.

Some classmates will have paid plans. That's not an advantage the rubric rewards: the largest block of points on the Ship-It project is for **finding and fixing what the agent got wrong**, and a better model just means you have to look harder.

If a tool limit is blocking you, tell me. That's a logistics problem, not a personal failing, and it has a solution.

---

## A closing thought

The students who will do best in this field over the next decade are not the ones who use AI the most, or the least. They're the ones who can look at fluent, confident, well-formatted output and say **"no, that's wrong, and here's why."**

That's a skill. It's built by using these tools constantly *and* by knowing enough to catch them. This course is trying to give you both at once.
