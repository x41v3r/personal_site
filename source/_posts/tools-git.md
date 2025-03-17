---
title: Git
date: 2025-03-06 20:51:36
categories:
- Tools
tags:
---

# 1 Getting Started



# 2 Git Basics

## 2.1 Getting a Git Repository

### 2.1.1 Initializing a Repository in an Existing Directory

Go to the project’s directory:

```bash
cd /home/user/my_project
```

and then type:

```bash
git init
```

> This creates a new subdirectory named **.git** that *contains all of the necessary repository files* — a Git repository skeleton.

If we want to start version-controlling existing files (as opposed to an empty directory), we should probably begin tracking those files and do an initial commit.

```bash
git add *.c
git add LICENSE
git commit -m 'Initial project version'
```

### 2.1.2 Cloning an Existing Repository

We can clone a repository with `git clone <url>`.

For example, clone the Git linkable library called libgit2:

```bash
git clone https://github.com/libgit2/libgit2
```

Undo the most recent git commit but keep the changes.

```bash
git reset --soft HEAD~1
```

Undo the most recent git commit and discard the changes.

```bash
git reset --hard HEAD~1
```

Merge a certain branch into the current branch.
