
# Gitflow Workflow Guide

This document explains the **Gitflow workflow**, a structured team-oriented way to manage branches, releases, and hotfixes.

---

## Overview
Gitflow introduces dedicated branches for different purposes:

- **`main`** → Production-ready code (what's live).
- **`develop`** → The next release in progress.
- **`feature/*`** → New features in development.
- **`release/*`** → Polished code for a new release.
- **`hotfix/*`** → Urgent fixes for production.

Visual flow:
```
main  → production
 │
 ├── hotfix/* → urgent fixes
 │
develop → next release in progress
 │
 ├── feature/* → new features
 │
 └── release/* → prep for production
```

---

## 1. Set Up
Create the `develop` branch:
```bash
git checkout -b develop
git push -u origin develop
```

---

## 2. Start a Feature
```bash
git checkout develop
git checkout -b feature/amazing-feature
# Work, edit files...
git add .
git commit -m "Add amazing feature"
git push -u origin feature/amazing-feature
```

When finished:
```bash
git checkout develop
git merge feature/amazing-feature
git push origin develop
git branch -d feature/amazing-feature
```

---

## 3. Prepare a Release
When `develop` is ready for release:
```bash
git checkout develop
git checkout -b release/1.0
# Polish code, fix bugs, update docs
git add .
git commit -m "Prepare release 1.0"
```

When ready for production:
```bash
git checkout main
git merge release/1.0
git push origin main
```

Tag the release:
```bash
git tag -a v1.0 -m "Release 1.0"
git push origin v1.0
```

Merge back to develop:
```bash
git checkout develop
git merge main
git push origin develop
```

---

## 4. Hotfixes
For critical bugs on production:
```bash
git checkout main
git checkout -b hotfix/critical-bug
# Fix the bug
git add .
git commit -m "Fix critical bug"
git checkout main
git merge hotfix/critical-bug
git tag -a v1.0.1 -m "Hotfix 1.0.1"
git push origin main --tags
git checkout develop
git merge hotfix/critical-bug
git push origin develop
```

---

## Summary
- **`main`**: Always stable, production-ready.
- **`develop`**: Next release.
- **`feature/*`**: For new features.
- **`release/*`**: Final prep for production.
- **`hotfix/*`**: Emergency fixes.

This structure makes it easy to manage releases, collaborate on features, and maintain a stable production branch.

