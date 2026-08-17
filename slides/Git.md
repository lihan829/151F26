---
layout: section
---
# Part 2: Git & Version Control

---

# Why Version Control?

<v-clicks>

- Track every change to your code over time
- Experiment safely with **branches** — no fear of breaking things
- Collaborate without overwriting each other's work
- Recover previous versions when something breaks
- Industry-standard skill for any programming job

</v-clicks>

<v-click>

> Git is the tool. **GitHub** is a website that hosts Git repositories online.

</v-click>

---

# Core Concepts

| Term | Meaning |
|---|---|
| **Repository (repo)** | A project folder tracked by Git |
| **Commit** | A saved snapshot of changes, with a message |
| **Branch** | An independent line of development |
| **Remote** | A version of the repo hosted elsewhere (e.g. GitHub) |
| **Clone** | Copy a remote repo to your machine |
| **Push / Pull** | Send / receive commits to and from a remote |

```mermaid
gitGraph
   commit id: "init"
   commit id: "add feature"
   branch dev
   commit id: "work in progress"
   checkout main
   merge dev
```

---

# Setting Up a Repository

```bash
# Configure your identity (once per machine)
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Start tracking a new project
git init

# Or copy an existing project from GitHub
git clone https://github.com/lihan829/151F26.git
```

---

# The Everyday Workflow

```bash
git status              # see what's changed
git add file.py         # stage a specific file
git add .                # stage everything

git commit -m "Add word frequency counter"

git push                 # send commits to GitHub
git pull                 # get latest commits from GitHub
```

<v-click>

```mermaid
flowchart LR
    A[Working Directory] -- git add --> B[Staging Area]
    B -- git commit --> C[Local Repository]
    C -- git push --> D[Remote / GitHub]
    D -- git pull --> A
```

</v-click>

---

# Branching & Merging

```bash
git branch feature-x        # create a branch
git checkout feature-x      # switch to it
git checkout -b feature-x   # create + switch in one step

# ... make changes, add, commit ...

git checkout main
git merge feature-x         # bring changes into main
git branch -d feature-x     # delete the branch
```

<v-click>

**Why branch?** Work on a lab or feature without touching the stable `main` branch until it's ready.

</v-click>

---

# Inspecting History

```bash
git log                 # full commit history
git log --oneline        # compact view
git diff                 # unstaged changes
git diff --staged        # staged changes
git show <commit-hash>   # details of one commit
```

```bash
$ git log --oneline
a1b2c3d Add regex lab solution
e4f5g6h Fix off-by-one in loop
h7i8j9k Initial commit
```

---

# GitHub Workflow (Homework Submission)

```bash
# 1. Clone your assignment repo
git clone https://github.com/your-org/lab1-yourname.git
cd lab1-yourname

# 2. Do your work, then check status
git status

# 3. Stage and commit
git add .
git commit -m "Complete Lab 1: variables and expressions"

# 4. Push to GitHub for submission
git push origin main
```

<v-click>

✅ Commit **often**, with clear messages — it's part of your grade trail!

</v-click>

---

# Common Pitfalls & Tips

<v-clicks>

- **Commit small, commit often** — easier to track down bugs
- Write clear commit messages: `"Fix bug"` ❌ → `"Fix off-by-one error in word counter"` ✅
- Always `git pull` before you start working, `git push` when you're done
- Use a `.gitignore` file to avoid committing junk (`__pycache__/`, `.DS_Store`, venvs)
- Merge conflicts aren't scary — Git tells you exactly which lines to resolve
- When in doubt: `git status` tells you where you are

</v-clicks>

---
layout: center
class: text-center
---

# Summary

<div class="grid grid-cols-2 gap-8 mt-8 text-left">
<div>

### 🐍 Python
- Variables, types, operators
- Control flow: `if`, `for`, `while`
- Functions with `def`

</div>
<div>

### 🔧 Git
- `add` → `commit` → `push`
- Branches for safe experimentation
- GitHub for collaboration & submission

</div>
</div>