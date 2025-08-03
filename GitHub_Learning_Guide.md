
# Git & GitHub Learning Guide

This document walks through the setup and basic workflows for using Git and GitHub, including setting up GitHub CLI, creating repositories, and working with feature branches.

---

## 1. Setup

### Install Git
Download and install from [https://git-scm.com/downloads](https://git-scm.com/downloads).  
Verify installation:
```bash
git --version
```

### Install GitHub CLI
#### Option A: Winget
```bash
winget install --id GitHub.cli
```
#### Option B: Manual Installer
Download from [https://cli.github.com/](https://cli.github.com/).

Verify installation:
```bash
gh --version
```

### Add `gh` to PATH (if needed)
1. Locate `gh.exe` (usually in `C:\Program Files\GitHub CLI\` or `C:\Users\<YourName>\AppData\Local\Programs\GitHub CLI\`).
2. Go to **System Properties** → **Advanced** → **Environment Variables** → **Path** → **Edit**.
3. Add the folder path containing `gh.exe`.
4. Restart your terminal.

### Authenticate GitHub CLI
```bash
gh auth login
```
Follow the prompts to log in via browser.

### Set Default Branch to `main`
```bash
git config --global init.defaultBranch main
```

---

## 2. Create Your First Repository

### Initialize Git in a Folder
```bash
cd E:\Github\Learning
git init
echo "# Learning Git" > README.md
git add README.md
git commit -m "Initial commit"
```

### Create and Link a GitHub Repository
```bash
gh repo create Learning --public --source=. --remote=origin --push
```

---

## 3. Daily Workflow
```bash
git add .                # Stage changes
git commit -m "Message"  # Commit changes
git push                 # Push to GitHub
git pull                 # Pull latest changes
```

---

## 4. Working with Features (Branching)

### Create a Feature Branch
```bash
git checkout main
git pull origin main
git checkout -b feature/new-feature
```

### Make Changes & Commit
```bash
# Edit files
git add <file>
git commit -m "Describe changes"
git push -u origin feature/new-feature
```

### Merge Feature Back to Main
```bash
git checkout main
git pull origin main
git merge feature/new-feature
git push origin main
```

### Delete Feature Branch (Optional)
```bash
git branch -d feature/new-feature
git push origin --delete feature/new-feature
```

---

## 5. Helpful Commands
- View history:  
  ```bash
  git log --oneline
  ```
- Undo staged changes:  
  ```bash
  git reset HEAD <file>
  ```
- Undo last commit (keep changes):  
  ```bash
  git reset --soft HEAD~1
  ```
- Create a new branch:  
  ```bash
  git checkout -b branch-name
  ```

---

You're now ready to start experimenting with Git & GitHub!

