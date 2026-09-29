# Git Stash Complete Notes

## Overview

`git stash` is a Git feature used to temporarily save uncommitted changes without creating a commit.

It allows developers to:

- Pause current work
- Switch branches safely
- Fix urgent issues
- Return later and continue from where they stopped

Git Stash is considered a **convenience tool**, not a mandatory Git workflow. Many developers use it frequently, while others rarely use it.

---

# Why Git Stash Exists

When working with Git branches, you may have uncommitted changes and suddenly need to switch branches.

Example:

```text
master
└── cat.py
```

Create a new branch:

```bash
git switch -c puppy
```

Make changes but do not commit them.

Now you need to switch back:

```bash
git switch master
```

Git can behave in two ways.

---

# Scenario 1: Changes Follow You

If there is no conflict, Git allows branch switching and brings the uncommitted changes along.

Example:

```bash
git switch master
```

Result:

```text
Modified files still exist.
```

Git Status:

```bash
git status
```

Output:

```text
modified: app.css
```

The changes are not attached to any commit, so they remain in your working directory.

---

# Scenario 2: Git Prevents Branch Switching

Git may detect that switching branches could overwrite files.

Example:

```bash
git switch master
```

Output:

```text
error: Your local changes to the following files would
be overwritten by checkout:

index.html

Please commit your changes or stash them before you switch branches.
```

Git prevents the switch to avoid losing work.

---

# The Problem

Suppose:

- You are halfway through a feature.
- Work is not ready for commit.
- You need to switch branches immediately.

Creating a temporary commit just to switch branches is often undesirable.

This is exactly the problem Git Stash solves.

---

# What Git Stash Does

Think of it as temporary storage.

```text
Working Directory
        │
        ▼
    git stash
        │
        ▼
 Temporary Stash Area
        │
        ▼
 Switch Branches Freely
        │
        ▼
 git stash pop
        │
        ▼
 Restore Previous Work
```

---

# Basic Stashing

Assume:

```bash
git status
```

Output:

```text
modified: app.css
```

Save the changes:

```bash
git stash
```

Result:

```text
Saved working directory and index state
```

Your working directory returns to the last committed state.

---

# Viewing Stashes

Display all stashes:

```bash
git stash list
```

Example:

```text
stash@{0}: WIP on rainbow
stash@{1}: WIP on rainbow
stash@{2}: WIP on rainbow
```

---

# Understanding Stash Indexes

Each stash receives an identifier.

```text
stash@{0}
```

Most recent stash.

```text
stash@{1}
```

Second most recent.

```text
stash@{2}
```

Third most recent.

Visual representation:

```text
Top of Stack
│
├── stash@{0}
├── stash@{1}
├── stash@{2}
└── Older Stashes
```

Git Stash behaves like a stack (LIFO).

LIFO = Last In First Out.

---

# Restoring Changes

## Method 1: Apply

Apply latest stash:

```bash
git stash apply
```

Result:

```text
Changes restored
Stash remains stored
```

The stash stays available for future use.

---

## Method 2: Pop

Restore latest stash:

```bash
git stash pop
```

Result:

```text
Changes restored
Stash removed
```

This is the most commonly used command.

---

# Apply a Specific Stash

Apply a particular stash:

```bash
git stash apply stash@{2}
```

Git restores only that stash.

Examples:

```bash
git stash apply stash@{0}
```

Latest stash.

```bash
git stash apply stash@{1}
```

Second stash.

```bash
git stash apply stash@{2}
```

Third stash.

---

# Difference Between Apply and Pop

## Apply

```bash
git stash apply
```

Behavior:

```text
Restore Changes
+
Keep Stash
```

---

## Pop

```bash
git stash pop
```

Behavior:

```text
Restore Changes
+
Delete Stash
```

---

# Working With Multiple Stashes

Git allows multiple entries.

Example:

### First Stash

```css
body {
    background-color: red;
}
```

```bash
git stash
```

---

### Second Stash

```css
body {
    background-color: orange;
}
```

```bash
git stash
```

---

### Third Stash

```css
body {
    background-color: yellow;
}
```

```bash
git stash
```

Now:

```bash
git stash list
```

might show:

```text
stash@{0} -> yellow
stash@{1} -> orange
stash@{2} -> red
```

---

# Stash Conflicts

Suppose current file contains:

```css
body {
    background-color: red;
}
```

Now apply another stash:

```bash
git stash apply stash@{1}
```

where stash@{1} contains:

```css
body {
    background-color: orange;
}
```

Git may create a conflict because both changes modify the same location.

The conflict must be resolved before continuing.

---

# Removing Individual Stashes

If you used:

```bash
git stash apply
```

the stash still exists.

Remove it manually:

```bash
git stash drop stash@{2}
```

Output:

```text
Dropped stash@{2}
```

Check:

```bash
git stash list
```

The selected stash disappears.

---

# Clearing All Stashes

Remove every stash entry:

```bash
git stash clear
```

Verify:

```bash
git stash list
```

Output:

```text
(no output)
```

Meaning:

```text
Stash is empty.
```

---

# Drop vs Clear

## Drop

Removes one stash.

```bash
git stash drop stash@{1}
```

---

## Clear

Removes all stashes.

```bash
git stash clear
```

---

# Practical Example - Website Project

Initial commit:

```bash
git add .
git commit -m "create index.html and app.css"
```

Create branch:

```bash
git switch -c purple
```

Add CSS:

```css
h1 {
    color: purple;
}

body {
    background-color: lavender;
}
```

Check:

```bash
git status
```

Output:

```text
modified: app.css
```

Need to switch branches?

```bash
git stash
```

Switch:

```bash
git switch master
```

Return later:

```bash