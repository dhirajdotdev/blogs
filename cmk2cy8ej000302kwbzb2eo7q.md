---
title: "Git for Beginners: Basics and Essential Commands"
seoTitle: "Git Basics: Essential Commands for Beginners"
seoDescription: "Learn Git with our beginner's guide. Understand version control, essential commands, and workflows to track and manage your project effectively"
datePublished: 2026-01-06T08:59:01.771Z
cuid: cmk2cy8ej000302kwbzb2eo7q
slug: git-basics-and-essential-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1767514551303/feb4671e-523e-4a26-a0e2-5902b52ce300.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1767689866065/e8f88e66-b24b-4c0d-8445-8eac498ec05e.png
tags: software-development, programming-blogs, github, opensource, version-control, git, coding, devops, programming-ciovqvfcb008mb253jrczo9ye, chaicode

---

Git is the tool that keeps track of how a project changes over time.

It helps developers save progress understand past changes and work on code without fear of losing it.

---

## What Is Git?

Git is a version control system that tracks changes in code.

In simple terms Git maintains a history of a project. Every change can be saved reviewed or undone later. Instead of copying folders or creating manual backups Git provides a structured way to manage how code evolves.

Git works locally on a developer’s machine. An internet connection is not required to start using Git. Everything related to the project’s history is stored inside a hidden `.git` folder.

---

## Why Git Is Used

Without Git developers rely on sharing ZIP files using multiple file names and creating manual backups.

As projects grow files change frequently. Bugs appear features stop working and it becomes difficult to identify when a problem was introduced.

Git removes this problem. It records what changed and when making it easier to find bugs and safer to experiment with code.

---

## Git Basics and Core Terminologies

### Repository (Repo)

A repository is a project that Git is tracking.

When developers run `git init`, Git creates a `.git` folder inside the project. This folder stores the complete history of changes made to that project.

---

### Commit

A commit records how the project looks at a specific point in its history.

Each commit represents a moment where developers decided that the current state of the code is worth saving. Commits include a unique ID a message and a position in the project’s history.

---

### Branch

A branch is a separate line of development.

Branches allow developers to work on features or experiments without affecting the main codebase. This makes parallel development possible and keeps changes isolated until they are ready.

---

### HEAD

HEAD points to the current position in the project’s history.

In simple terms HEAD tells Git which commit is currently checked out.

---

## File States in Git

Files tracked by Git move through different states.

* **U - Untracked** (Red)  
    Git sees the file but it is not tracked yet.
    
* **M - Modified** (Red)  
    The file is tracked but it has changed after the last commit.
    
* **A - Added (Staged)** (Green)  
    The file is added to the staging area and ready to be committed.
    
* **D - Deleted** (Red)  
    A tracked file has been removed.
    
* **R - Renamed** (Green)  
    A file was renamed and Git keeps its history.
    
* **C - Copied** (Green)  
    A file was copied from another tracked file.
    
* **U - Unmerged** (Red)  
    A merge conflict exists and needs manual resolution.
    
* **Clean** (White)  
    No pending changes. Everything is committed.
    

---

### File State Flow

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767626143156/1c352a4c-67a3-4c2d-bf99-1df47d0f8be9.png align="center")

---

## Git Workflow (How Git Actually Works)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767626263173/16efe232-2b29-4366-ad45-fd9f3a5de09e.png align="center")

### Workflow Diagram

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767627623160/7693199d-8f60-41c0-9c90-5e983d35fb81.png align="center")

---

## Essential Git Commands (With Examples)

### git init

Initializes a new Git repository.

```plaintext

git init
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767540835132/7e2d73f7-35e0-438a-9b96-a399a65bcf1b.png align="center")

This command is usually run once when starting a project.

---

### git status

Shows the current state of files.

```plaintext

git status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767602906524/336fb246-33fd-4a1a-93b3-f59729fc589a.png align="center")

It tells developers:

* Which files are untracked
    
* Which files are modified
    
* What is staged for commit
    

---

### git add `<fileName>`

Adds files to the staging area.

```plaintext

git add index.js
git add .
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767602981646/c64b8e8a-2d02-4221-86ca-4b8463c88b1b.png align="center")

This tells Git which changes should be included in the next commit.

---

### git commit -m "message"

Creates a commit.

```plaintext

git commit -m "add initial files"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767603031124/62a96b8f-82c6-45a1-9a52-6444bb3374b5.png align="center")

A good commit message explains **what** changed.

---

### git log --oneline

Shows commit history in a short format.

```plaintext

git log --oneline
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767624568943/757092ab-b22f-4187-99fc-8d030dcc7dba.png align="center")

---

### Commit History Flow

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767624539631/56f87bbf-8c45-4bcb-b07f-9b30a6ada7b4.png align="center")

Each commit builds on the previous one.

---

### git diff

Shows changes that are not committed yet.

```plaintext

git diff
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767603723157/4b3c037c-bd0b-45d6-9e3f-fcb137109aca.png align="center")

Useful for reviewing changes before committing.

---

### git revert `<commit-hash>`

Safely undoes a commit by creating a new commit.

```plaintext

git revert 05a7dd3
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767625243102/b3734842-128c-4865-a837-a4e05b7f2625.png align="center")

---

### git reset --hard `<commit-hash>`

Moves the project back to a specific commit.

```plaintext

git reset --hard 05a7dd3
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767625360456/ad81fcc1-4d7d-47da-96b9-0caddea5e98b.png align="center")

This removes all changes after that commit.

---

### git branch

Lists available branches.

```plaintext

git branch
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1767625735612/018ee64b-ca0c-42e7-bc36-588deb120e98.png align="center")

Branches help manage parallel development.

---

## A Basic Git Workflow From Scratch

```plaintext

git init
git status
git add .
git commit -m "initial commit"
git log --oneline
```

This is the most common Git workflow used in real projects.