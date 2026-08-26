# COSC 10001: The Computer Science Experience

**Texas Christian University · Fall 2026 · Wednesdays 9:00–9:50 AM · RJH 333** Instructor: Bingyang Wei · First class: **Wed, Aug 26, 2026**

### 📖 Read the course site: **<https://washingtonwei.github.io/cosc-10001/>**

This repository is the source of that site. It is also, deliberately, a teaching tool: we read its history together in the Git session. The in-class pull request exercise runs against a separate practice repo, so nothing the class does lands here, but typo fixes are welcome any time.

---

## Course materials

| Page | What it is |
|---|---|
| [Start Here](docs/index.md) | The landing page, and the Week 1 checklist |
| [Syllabus](docs/syllabus.md) | Grading, policies, expectations |
| [Schedule](docs/schedule.md) | Week-by-week plan and every deadline |
| [AI Policy](docs/ai-policy.md) | How to use AI here, and how to disclose it |
| [What to Read](docs/reading.md) | Newsletters, podcasts, and channels worth following |
| [Opportunities](docs/opportunities.md) | Hackathons, research, internships, clubs, and when to act |
| [Ship-It Project](docs/ship-it.md) | The build project, 20% of your grade |
| [Accounts & Tools](docs/tool-setup.md) | Every account and install, in order |
| [IntelliJ + Karel](docs/setup-intellij.md) | The editor, and the robot running inside it |
| [Windows Terminal Setup](docs/setup-windows.md) | WezTerm + PowerShell 7 |
| [macOS Terminal Setup](docs/setup-macos.md) | Ghostty + zsh |

---

## Found a typo? Fix it.

You do not need permission, and you do not need to wait for the open-source session:

1. Open the page on the site and click the ✏️ pencil icon (or find the file in `docs/`).
2. Edit it. GitHub will fork the repo for you automatically.
3. Open a pull request describing what you changed and why.

If it's correct, it gets merged, and the site rebuilds itself within a minute or two. Your name goes in the history of a real course website. That's not a practice exercise; it's the same workflow used by every open-source project you'll ever contribute to.

---

## Building the site locally

Optional. You never need this to read the course materials or to fix a typo.

```bash
pip install -r requirements.txt
mkdocs serve
```

Then open <http://127.0.0.1:8000>. The site rebuilds as you save.

The published site is built by [GitHub Actions](.github/workflows/pages.yml) on every push to `main`. Builds run with `--strict`, so a broken internal link fails the build instead of shipping.

---

## License

Course materials © 2026 Bingyang Wei, Texas Christian University.
