***

# 📘 Git Fundamentals – Complete Beginner Guide

<https://miro.medium.com/v2/resize:fit:1400/1*Hh4bJmFJ0QxW3C3R6TSgtw.png>

***

# 🚀 Introduction

This document provides a **complete, beginner-friendly guide to Git**, covering:

* ✅ What Git is
* ✅ What repositories are
* ✅ How Git works internally
* ✅ Complete workflow (Add → Commit → Log)
* ✅ Commands explained step-by-step
* ✅ Real practice example

***

# 🧠 What is Git?

Git is a **version control system** used to:

* Track changes in files
* Maintain history of a project
* Allow collaboration between developers

***

# 📂 What is a Repository (Repo)?

A **repository** is:

> A folder that Git tracks including its history.

### ✅ Key Points:

* Each repo has its **own history**
* Repos are **independent**
* You can have **multiple repos** on your system

***

# ⚙️ Installing Git vs Using Git

* Installing Git:
  * ✅ Adds Git to your system
* Using Git:
  * ❌ Does NOT happen automatically
  * ✅ You must initialize a repo

***

# 🏗️ Creating a Git Repository

## ✅ Step 1: Create folder

```bash
mkdir MyProject
cd MyProject
```

## ✅ Step 2: Initialize repository

```bash
git init
```

### ✅ Output:

```
Initialized empty Git repository in /path/MyProject
```

***

# 🔍 What Happens Internally?

After `git init`:

* A hidden folder is created:

```
.git
```

***

## 📁 What is `.git` Folder?

This is the **heart of Git**:

* Stores:
  * Commit history
  * Configuration
  * Project snapshots

***

## ⚠️ Important Warning

```bash
rm -rf .git
```

🚫 Deletes entire Git history permanently

***

# 📊 Checking Git Status

```bash
git status
```

***

## ✅ Possible Outputs:

### ❌ Not a repo:

```
fatal: not a git repository
```

### ✅ In repo:

```
On branch main
nothing to commit, working tree clean
```

***

# 🌳 Git Tracks Entire Directory

Once initialized:

* Git tracks:
  * All files
  * Subfolders
  * Nested directories

***

## ⚠️ Avoid Nested Repositories

### ❌ Wrong:

```
Project/
   .git
   subfolder/
       .git   ❌
```

➡️ Causes confusion

***

## ✅ Rule:

* One project = One repository

***

# 🔄 Core Git Workflow

```
Working Directory → Staging Area → Repository
```

***

# 🧩 3 Important Areas

***

## 1️⃣ Working Directory

* Your files (where you work)
* Example:
  * edit code
  * create files

***

## 2️⃣ Staging Area

* Temporary holding area
* You select changes before commit

***

## 3️⃣ Repository (.git)

* Stores permanent history
* Commits are saved here

***

# ✏️ Step 1: Make Changes

Example:

```bash
touch file.txt
```

Edit file → Save it

***

# ➕ Step 2: Stage Changes (`git add`)

## ✅ Add single file:

```bash
git add file.txt
```

## ✅ Add multiple files:

```bash
git add file1.txt file2.txt
```

## ✅ Add all files:

```bash
git add .
```

***

## 🔎 What does `git add` do?

* Moves files from:

```
Working Directory → Staging Area
```

* Does NOT commit

***

## 💡 Concept

> Think of `git add` as selecting files with **tweezers**

***

# ✅ Step 3: Commit Changes (`git commit`)

## ✅ Recommended command:

```bash
git commit -m "Your message"
```

***

## 📝 What is a Commit?

A commit is:

> A snapshot (checkpoint) of your project at a moment in time

***

## ✅ Commit Includes:

* Selected changes
* Commit message

***

## ✅ Example:

```bash
git commit -m "Add login feature"
```

***

# 🧾 Commit Message Guidelines

✅ Good:

* `Add navbar`
* `Fix bug in login`
* `Create user model`

❌ Bad:

* `update`
* `changes`

***

# ✅ After Commit

Run:

```bash
git status
```

Output:

```
nothing to commit, working tree clean
```

***

## ✅ Meaning:

* No pending changes
* Everything is saved

***

# 📜 View History (`git log`)

```bash
git log
```

***

## ✅ Shows:

* Commit ID (hash)
* Author
* Date
* Message

***

# 🔁 Full Workflow (Repeat Cycle)

```
1. Make changes
2. git status
3. git add
4. git commit
5. git log
6. Repeat
```

***

# 🧪 Practice Project – Shopping List

***

## ✅ Step 1: Setup Project

```bash
mkdir shopping
cd shopping
git init
```

***

## ✅ Step 2: Create Files

```bash
touch yard.txt
touch groceries.txt
```

***

## ✅ Step 3: First Commit

```bash
git add yard.txt groceries.txt
git commit -m "Create yard and groceries lists"
```

***

## ✅ Step 4: Add Content

### yard.txt:

```
2 bags of potting soil
1 bag of worm castings
```

### groceries.txt:

```
Tomatoes
Onions
Garlic
```

***

## ✅ Step 5: Commit Only Groceries

```bash
git add groceries.txt
git commit -m "Add ingredients for tomato soup"
```

***

## ✅ Step 6: Commit Yard File

```bash
git add yard.txt
git commit -m "Add items needed for garden box"
```

***

## ✅ Step 7: Modify Both Files

* Add:

```
Potatoes
```

* Update:

```
2 bags → 3 bags
```

***

## ✅ Step 8: Commit All

```bash
git add .
git commit -m "Add items needed to grow potatoes"
```

***

## ✅ Step 9: View History

```bash
git log
```

***

# 🎯 Key Concepts Summary

✅ Repository = Project + History  
✅ `.git` = Stores everything  
✅ `git status` = Check changes  
✅ `git add` = Select changes  
✅ `git commit` = Save snapshot  
✅ `git log` = View history

***

# 🚨 Important Rules

* ✅ One repo per project
* ✅ Always run `git status`
* ✅ Write meaningful commit messages
* ✅ Avoid nested repositories

***

# 🧠 Final Understanding

Git is about:

> Tracking your work step-by-step with clean history

***

## 💡 Core Idea:

```
Work → Add → Commit → Repeat
```

***

# 🎉 You’re Ready!

You now understand the **complete foundational workflow of Git** 🚀

***

