# Professional Foundations, Step by Step

**Due Wed, Sep 30 · 10% of your grade.** Five small things that together make you findable as a computer scientist. None of them is hard, and two of them you may have finished in the Git session without noticing.

Do them in order: each one uses something from the one before. Budget about three hours in total, most of it on the résumé.

!!! tip "Graded on completion, professionalism, and attention to detail"
    In plain English: **everything exists, nothing is embarrassing, and the links work.** Nobody expects a polished professional at eighteen. We do expect your real name spelled the same way everywhere, no typos in your headline, and no link that goes to a 404.

---

## 1. GitHub account and the Student Developer Pack

You probably did this in the first week. If you did, and the Pack shows as approved, skip to step 2.

1. Follow [Accounts & Tools, sections 1 and 2](tool-setup.md#1-github-account). They cover choosing a username, which email to use, and the three reasons Pack applications get rejected.
2. **Check that it worked:** look for the email from GitHub Education saying your application was approved. It can take a few days.
3. Still waiting or rejected? **Submit anyway, and say so.** A pending application counts; no application does not. Bring a rejection email to office hours and we'll fix it together.

✅ **You're done when** your Pack is approved or you have a pending application you can screenshot.

---

## 2. A public repository with a real `README.md`

**Your Karel repository counts**, the one you pushed in the Git session. But it needs one fix first: the `README.md` in it is the one *we* wrote, starting with *"This folder holds a robot."* A meaningful README is one *you* wrote about *your* project.

### Haven't pushed your Karel repo yet? Do this first

Missed the Git session, or ran out of time? Start here. It takes about fifteen minutes. If you got partway in class, pick up where you stopped: running a step twice does no harm, except the one marked below.

**You need** your [terminal setup](setup-windows.md) finished ([macOS version](setup-macos.md)), because Git comes from there.

**a. Make an empty repository on github.com.**

1. Sign in at <https://github.com>, click **+** (top right) → **New repository**.
2. **Repository name:** `karel-starter`.
3. Choose **Public**.
4. **Leave every box unticked:** no README, no `.gitignore`, no license. Your laptop already has the files, and a README made here will clash with yours at step d.
5. Click **Create repository**. Leave that page open; you need your username from it in a minute.

**b. Open a terminal inside your Karel folder.** Open the folder in IntelliJ, then click the **Terminal** icon at the bottom left (or **View → Tool Windows → Terminal**). It opens already in the right folder. Check with `git status`: anything but `not a git repository` means you have done step c before, and that's fine.

**c. Save your work as a first commit.**

```
git init
git add .
git commit -m "Karel reaches the beeper"
```

`nothing to commit` means you did this in class. Carry on.

**d. Connect your folder to GitHub and push.** Replace `USERNAME` with your GitHub username:

```
git remote add origin https://github.com/USERNAME/karel-starter.git
git push -u origin main
```

⚠️ Run `git remote add` **once**. If it says `remote origin already exists`, you did it before; skip straight to `git push -u origin main`.

**e. Sign in, the first time only.**

- **Windows:** a browser window opens asking you to sign in to GitHub. Do it, and the push finishes by itself.
- **macOS:** your terminal asks for a password and then fails, because GitHub stopped accepting passwords in 2021. Fix it once with these two commands, then run `git push -u origin main` again:

    ```
    brew install gh
    gh auth login
    ```

    Answer its questions: **GitHub.com**, **HTTPS**, **Yes** to authenticate Git, then **Login with a web browser**. It shows a code; paste it into the page it opens.

**f. Check that it worked.** Refresh your repository page on github.com. Your files should be there instead of the empty-repository instructions. From now on, sending changes up is always the same three steps: `git add`, `git commit`, `git push`.

**If it fights you:**

- `rejected ... (fetch first)`: you ticked *Add a README* in step a. Easiest fix: on github.com, **Settings** → scroll to the bottom → **Delete this repository**, then do step a again with every box unticked. Then `git push -u origin main`.
- `src refspec main does not match any`: if `git commit` in step c printed an error, fix that first. Otherwise your branch is called `master`, because the `init.defaultBranch main` line from the terminal setup was skipped. Run `git branch -M main`, then push again.
- Anything else: copy the exact error and send it to your peer mentor, with which step you were on.

### Now make the README yours

1. Open your Karel folder in IntelliJ, and open `README.md`.
2. **Replace everything in it** with your own version. Four short parts are enough:
    - A title, like `# Karel the Robot`
    - One or two sentences: what this is, in your words. *"My work from the Karel weeks of COSC 10001 at TCU. Karel is a robot that only knows four commands."*
    - **How to run it.** Open the folder in IntelliJ and press the green button, or `run.ps1` on Windows and `run.sh` on macOS
    - **What you learned**, in two or three bullet points. Be specific: *"Karel has no `turnRight()`, so I built one from three `turnLeft()` calls"* beats *"I learned programming"*
3. Save, then commit and push, exactly as in the Git session:

    ```
    git add README.md
    git commit -m "Write my own README"
    git push
    ```

4. **Check that it worked:** open your repository on github.com in a browser. Your new README should appear below the list of files. Also check the repository says **Public** next to its name.

✅ **You're done when** `https://github.com/YOUR-USERNAME/YOUR-REPO` loads in a private browser window and shows a README you wrote.

---

## 3. Your GitHub profile README

A repository with **exactly the same name as your username** is special: GitHub shows its README at the top of your profile page. It is the first thing anyone sees when they look you up, including recruiters in three years.

You can do this entirely in the browser. No terminal needed.

1. On github.com, click **+** (top right) → **New repository**.
2. For **Repository name**, type your username exactly, capitals and all. GitHub will say *"You found a secret!"*. That's how you know you got it right.
3. Set it to **Public**, and tick **Add a README file**. Click **Create repository**.
4. Click the pencil icon on the README to edit it. Delete the placeholder text and write your own. Three short parts are enough:
    - **Who you are:** name, *"first-year Computer Science student at TCU, Class of 2030,"* and where you're from if you like
    - **What you're curious about:** a field of CS, a game, a problem you'd like solved. One or two sentences
    - **What you're building, or want to build:** it can be the Karel repo, your Ship-It idea, or something you daydream about
5. Click **Commit changes**.
6. **Check that it worked:** open `https://github.com/YOUR-USERNAME`. Your README should be at the top of the page.

Your profile is public. **Do not put your phone number, home address, or student ID on it.** A LinkedIn link is fine, once you have one (step 4).

✅ **You're done when** `https://github.com/YOUR-USERNAME` shows your README at the top.

---

## 4. A LinkedIn profile

LinkedIn is where internship recruiters look first. Already have a profile? Update it using the list below.

1. Sign up at <https://www.linkedin.com>. Use your personal email, not `@tcu.edu`: this profile should outlive your time at TCU.
2. Fill in these five things. They are what we check:
    - **A photo** of your face, reasonably lit, just you. A phone photo against a plain wall is fine
    - **Headline:** *"Computer Science student at TCU"*. That's plenty
    - **Education:** Texas Christian University, Bachelor of Science, Computer Science, 2026 – 2030
    - **Your GitHub link:** click **Edit profile** (the pencil) → **Contact info** → **Website**, and add `https://github.com/YOUR-USERNAME`
    - **Your custom URL:** click **Public profile & URL** (on the right of your profile page) → the pencil next to your URL, and change it to your name, like `linkedin.com/in/firstname-lastname`
3. Optional but worth two minutes: an **About** section of two or three sentences, which can borrow from your profile README.
4. **Make your first connections.** Search LinkedIn by name, click **Connect** on each person, and click **Follow** on the page:
    - **Bingyang Wei**, your instructor
    - **Your peer mentor**
    - **TCU Computer Science**: <https://www.linkedin.com/school/tcu-computer-science>
5. **Check that it worked:** open your custom URL in a private browser window. It should show your name, photo, and headline.

✅ **You're done when** your custom LinkedIn URL shows those five things, and you've sent your two connection requests and followed TCU Computer Science.

---

## 5. A draft technical résumé

The word that matters is **draft**. You are a first-year in September; nobody expects much on it yet. The point is to have the file, in the right shape, so that adding to it later is easy. We'll improve it together in the Careers session on Wed, Dec 2.

**One page, saved as a PDF.** Use the [TCU Center for Career & Professional Development](https://careers.tcu.edu) templates, or any clean one-column template in Word or Google Docs. Skip the fancy two-column designs: the software companies use to read résumés often scrambles them.

Put these sections in this order:

1. **Your name and contact line:** email, phone, city, your LinkedIn URL, your GitHub URL.
2. **Education:** Texas Christian University, B.S. in Computer Science, *Expected May 2030*. Add **Relevant coursework**: Intro to Programming, The Computer Science Experience.
3. **Projects:** your Karel repository, with its link and one or two bullet points saying what you did. Start each bullet with a verb: *Wrote*, *Designed*, *Built*.
4. **Experience:** any job, paid or not. Lifeguard, barista, and tutor all count: they show you show up.
5. **Skills:** only things you have actually used. Java, Git, GitHub, IntelliJ, and GitHub Copilot are all fair now.
6. **Activities** (optional): clubs, sports, volunteering.

Before you save the PDF, check three things: every link works, your name matches LinkedIn and GitHub, and a friend has read it once for typos.

🟢 **AI is welcome here.** Ask your agent to tighten your bullet points or catch typos. [The AI policy](ai-policy.md#assignment-by-assignment) calls this Green. **Every word on it has to be true**: if an agent adds a skill you don't have, delete it, because an interviewer will ask about it.

✅ **You're done when** you have a one-page PDF named `Firstname-Lastname-Resume.pdf`.

---

## How to submit

**Email it to your peer mentor by Wed, Sep 30.** One email, with the résumé attached and everything else pasted in. Don't have your mentor's email address? Ask your pod or ask in Slack.

**Subject:** `Professional Foundations: Firstname Lastname`

**Body**, copy this and fill it in:

```
Student Pack: approved (or: pending since Sep __)
Repository: https://github.com/YOUR-USERNAME/YOUR-REPO
Profile README: https://github.com/YOUR-USERNAME
LinkedIn: https://www.linkedin.com/in/YOUR-CUSTOM-URL
Résumé: attached
```

**Last check before you send:** open every link in a private browser window, where you're not signed in. That's how your mentor will see them, and it catches the most common mistake, a repository that's still private.

Stuck on any step? Ask in Slack or ask your peer mentor. The fastest way to get help is to say which step, what you tried, and what happened.
