# IntelliJ IDEA + Karel

**This is the editor you'll use in this course, and this page gets it working with the Karel robot.**

**Do it before Wed, Sep 2.** It takes about twenty minutes, most of which is a download bar. **If something breaks, stop and come to class with it broken.** That is genuinely the assignment, and the session is built around fixing exactly this.

> **Wait, my programming class uses VS Code.** Correct, and that's on purpose. Both editors run the same two commands underneath, you'll watch that happen in class, and being able to sit down in front of two editors instead of one is a small real advantage you get for almost no effort. Keep VS Code for Intro to Programming. Use IntelliJ here.

---

## Before you start

**You need two things, and neither of them is Java.**

1. The **`karel-starter` zip**, downloaded from TCU Online and unzipped somewhere sensible. Not your Downloads folder, which is where projects go to die. Somewhere like `Documents/cs10001/karel-starter`.
2. About twenty minutes and an internet connection that isn't fighting you.

> **You do not have to install Java yourself, and this is the main reason this course uses IntelliJ.** Java comes as something called a **JDK**, and getting one onto a laptop by hand is the single most common way a first week goes wrong. IntelliJ fetches one for you from a dialog box, in about two minutes. **[Step 4](#4-give-it-a-java-to-run-on) walks through it.**

**You do not need a terminal for this page, or for the Karel session.** You'll set up a proper terminal before the **Git session on Wed, Sep 9**, and [that guide](tool-setup.md#5-a-terminal-git-and-nodejs) is waiting for you when you get there.

---

## 1. Download IntelliJ IDEA

Go to **<https://www.jetbrains.com/idea/download/>** and download IntelliJ IDEA for your machine.

**There is only one download now, and it is called just IntelliJ IDEA.** If you find an older guide telling you to pick "Community Edition", ignore it: JetBrains merged the two into a single installer in late 2025, and the last Community build was frozen then. Don't go digging for it in an archive, you'd be installing something a year out of date.

The site usually detects your machine and offers the right file. If you want to check it guessed right:

| Your machine | Pick |
|---|---|
| **Windows**, the normal kind | The `.exe` installer |
| **Windows on ARM** (Snapdragon, and you'd know) | The **ARM64** `.exe` |
| **Mac, Apple silicon** (M1 through M4, so almost certainly you) | The **Apple Silicon** `.dmg` |
| **Mac, Intel** (2020 or older) | The **Intel** `.dmg` |

Not sure which Mac you have? Apple menu → **About This Mac**. If the chip line says "Apple", you want Apple Silicon.

Run the installer and accept the defaults. On Windows, ticking "Add bin folder to PATH" is harmless and occasionally handy.

---

## 2. First launch, and the money question

When IntelliJ opens for the first time it will offer you a **30-day trial of IntelliJ IDEA Ultimate**.

**You do not need it. Everything in this course works on the free version, forever.** Take the trial or skip it, whichever you like. When 30 days are up the IDE keeps working; some features you were never using switch off, and Karel is entirely unaffected.

> **This is the promise from the syllabus in practice: no assignment in this course requires a paid subscription to anything.** If any instruction anywhere seems to say otherwise, it's wrong, and I want to know about it.

### Worth five minutes: get Ultimate free

**You are a student, so JetBrains gives you Ultimate at no cost, along with every other IDE they make.** PyCharm, WebStorm, CLion, DataGrip, the lot. That is a genuinely good deal and it lasts as long as you're enrolled.

Apply at **<https://www.jetbrains.com/community/education/>**. You can verify with:

- **your TCU email address**, which is the fastest route and the one to use
- your [GitHub Student Developer Pack](tool-setup.md#2-github-student-developer-pack), if it has already been approved
- an ISIC card or other proof of enrollment

**Do not let this block you.** The Pack can take days to come through, and this course never needs it. Install IntelliJ, get Karel running, and apply for the license whenever. The TCU email route doesn't depend on the Pack at all, so you can do it today.

> **One thing to know now so it doesn't surprise you in a year:** the educational license runs **one year at a time** and you renew it by confirming you're still a student. JetBrains emails you about two weeks before it lapses, and renewal is automatic once you verify. This is not a trial running out.

---

## 3. Open `karel-starter`

On the welcome screen, click **Open**. Not *New Project*.

**Select the `karel-starter` folder itself**, the one containing `MyKarel.java`. Not the zip, not a file inside it, not the folder above it. Click **OK**, and trust the project if it asks.

You should now see the file list on the left with `MyKarel.java`, a `lib/` folder holding `karel.jar`, `worlds/`, and the two run scripts. The title bar should say *karel-starter*.

**If IntelliJ asks which JDK to use, or shows a yellow banner about one, don't panic and don't guess.** That's step 4, and it's next.

---

## 4. Give it a Java to run on

IntelliJ is the workshop. The **JDK** is the machine that actually turns your typing into a running program, and it's a separate download. You need one, and IntelliJ will go and get it for you.

Open `MyKarel.java` from the file list on the left. **If a yellow banner appears across the top of the editor saying "Project SDK is not defined", click `Setup SDK` on it** and go to the version table below.

**No banner? Do it by hand.** Same twenty seconds:

1. **File → Project Structure...** (Windows: `Ctrl+Alt+Shift+S` · macOS: `⌘ ;`)
2. Under **Project Settings** on the left, click **Project**.
3. Open the **SDK** dropdown.
4. Click **Download JDK...**, near the bottom of that list.

Either way, you land in the same small dialog. Fill it in like this:

| Field | Choose |
|---|---|
| **Version** | `26` |
| **Vendor** | **Oracle OpenJDK** |
| **Location** | Leave it exactly as it is |

Click **Download**. A progress bar runs for a minute or two. When it finishes, the **SDK** box reads something like `openjdk-26 Oracle OpenJDK version 26.0.2`. Click **OK**.

> **Where did that just go?** Into a hidden folder called `.jdks` in your home directory, which belongs to IntelliJ rather than to your whole computer. That's deliberate and it's good news: it **cannot collide with the Java you install for Intro to Programming**. Having two Javas on a laptop sounds alarming and usually is. These two never meet.

**Any version 17 or newer runs Karel**, so if `26` isn't offered for your machine, take the highest number in the list and carry on. We name 26 so that everyone in the room is looking at the same version number when something goes wrong.

---

## 5. Tell IntelliJ where the robot lives

Open `MyKarel.java`. **The line `import stanford.karel.*;` will have a red underline, and the word `Karel` will be red too.**

**Nothing is broken.** Your program is fine. IntelliJ simply doesn't know yet that the robot library exists, because `karel.jar` is just a file sitting in a folder as far as it's concerned.

So tell it:

1. In the file list on the left, **click the arrow next to `lib` to open it**, then **right-click `karel.jar`** inside.
2. Choose **Add as Library...**
3. Leave the options alone and click **OK**.

The red goes away, usually within a second or two.

> **This is worth thirty seconds of your attention, because it's the same idea twice.** In class you'll watch Karel start from the terminal with `javac -cp lib/karel.jar`, where `-cp` is short for "classpath" and means "here's where to find code I didn't write." **Add as Library** is that exact instruction, given with a mouse instead of a keyboard. Two ways to say one thing. Once you see that, a lot of tooling stops being mysterious.

---

## 6. Run it

Open `MyKarel.java` and look in the left margin, next to `public class MyKarel`. There's a small green **▶**.

Click it and choose **Run 'MyKarel.main()'**.

A window opens with a grid and a small robot in the bottom-left corner. **Press Start.** Karel takes two steps and stops.

**That's it. You're set up.** From here on, that green arrow is how you run your program.

---

## When it breaks

It will break for somebody, and that somebody is not doing anything wrong.

**`import stanford.karel.*` is still red after Add as Library.** Give it a moment to reindex. If it persists, **File → Invalidate Caches... → Invalidate and Restart**. This is IntelliJ's version of turning it off and on again, and it genuinely works.

**There's no green ▶ next to the class.** Usually the library step hasn't taken yet, because IntelliJ won't offer to run a class it can't fully resolve. Fix the red first and the arrow appears.

**"Project SDK is not defined."** IntelliJ doesn't know which Java to use yet. That's [step 4](#4-give-it-a-java-to-run-on), and it is a normal thing to see, not a sign anything is wrong.

**There's no `Download JDK...` in the SDK dropdown.** Scroll the list: it sits at the very bottom, under any JDKs already on your machine, and it's easy to miss.

**The JDK download fails or stalls.** Almost always the network. Try again off campus wifi, or on your phone's hotspot. If it fails twice, stop and bring the laptop to class rather than hunting for a manual installer.

**The window opens but Karel doesn't move.** You probably haven't pressed **Start**.

**Karel walks into a wall.** Nothing is broken. Your instructions were wrong, which is a different and much more interesting problem. The computer did exactly what you said, not what you meant. You're going to hear that sentence a lot.

**Everything worked yesterday and doesn't today.** Close IntelliJ completely and reopen it. Roughly ninety percent of the time this is the whole fix, which is either reassuring or infuriating depending on your mood.

**Still stuck?** [How to Ask for Help](syllabus.md#how-to-ask-for-help) is a real section with a real format, and using it gets you a fast answer. Post the exact error text, not "it doesn't work." Then come to class with it broken.
