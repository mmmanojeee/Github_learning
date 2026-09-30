# Git Undoing Changes: Restore, Reset, and Revert

## Overview

This section covers a collection of Git commands that help you:

- Undo changes
- Recover previous versions of files
- Move back to earlier states of a repository
- Reverse commits safely
- Fix mistakes in local and shared repositories

Commands covered:

```bash
git restore
git reset
git reset --hard
git revert
```

---

# Why These Commands Exist

Most day-to-day Git work revolves around:

```bash
git add
git commit
git branch
git switch
git merge
git diff
```

However, developers occasionally make mistakes:

- Editing the wrong file
- Creating unwanted commits
- Committing on the wrong branch
- Needing to restore an earlier version of a file

The commands in this section help recover from those situations.

---

# Git Restore

## Purpose

`git restore` restores file contents.

It was introduced as a newer, more focused alternative to some uses of `git checkout`.

Historically:

```bash
git checkout
```

was used for many unrelated tasks.

Git introduced:

```bash
git switch
```

for branch switching and:

```bash
git restore
```

for restoring files.

---

## Restore File to Current HEAD

Example:

```bash
git restore dog.txt
```

This restores:

```text
dog.txt -> version stored in HEAD
```

Equivalent older syntax:

```bash
git checkout HEAD dog.txt
```

---

## Restore File from an Earlier Commit

Example:

```bash
git restore --source HEAD~2 dog.txt
```

Meaning:

```text
HEAD     = current commit
HEAD~1   = one commit back
HEAD~2   = two commits back
```

The file content becomes identical to how it looked two commits earlier.

---

## Restore Multiple Files

```bash
git restore --source HEAD~2 cat.txt dog.txt
```

Both files are restored from the same source commit.

---

## Important Warning

If changes have not been committed:

```bash
git restore file.txt
```

can permanently remove those local changes.

Git cannot recover work that was never committed.

---

## Does Restore Move HEAD?

No.

```bash
git restore --source HEAD~2 dog.txt
```

Changes:

✅ File content

Does NOT change:

❌ Current branch

❌ Commit history

❌ HEAD position

---

# Git Reset

## Purpose

`git reset` moves the current branch pointer backward.

Unlike restore, reset affects commit history.

---

## Basic Syntax

```bash
git reset <commit-hash>
```

Example:

```bash
git reset 4661abc
```

---

## What Happens?

Before:

```text
A → B → C → D → E (HEAD)
```

Run:

```bash
git reset C
```

After:

```text
A → B → C (HEAD)
```

Commits D and E disappear from the current branch history.

---

## Important Behavior

A normal reset removes commits but keeps the file changes.

### Before

```text
Commit D
Commit E
```

### After Reset

```text
D and E removed from history
Changes from D and E remain locally
```

This means your work is not lost.

---

## Real-World Scenario

You accidentally committed work on `master`.

```bash
git reset <good-commit>
git switch -c feature-branch
```

Then:

```bash
git add .
git commit -m "move work"
```

Your commits disappear from master while the work is preserved and can be committed on the correct branch.

---

# Git Reset --hard

## Purpose

A destructive version of reset.

Syntax:

```bash
git reset --hard <commit>
```

---

## What Happens?

Before:

```text
A → B → C → D → E (HEAD)
```

Run:

```bash
git reset --hard C
```

After:

```text
A → B → C (HEAD)
```

And:

```text
Changes from D and E are deleted
```

---

## Shortcuts

```bash
git reset --hard HEAD~1
```

Go back one commit.

```bash
git reset --hard HEAD~2
```

Go back two commits.

```bash
git reset --hard HEAD~3
```

Go back three commits.

---

## Warning

Use carefully.

`--hard` removes:

- Commit history
- Working directory changes
- Uncommitted modifications

Potentially unrecoverable.

---

## Branch-Specific Behavior

Reset affects only the current branch.

Example:

```text
master:
A → B → C → D

feature:
A → B → C → D
```

After:

```bash
git reset --hard C
```

Result:

```text
master:
A → B → C

feature:
A → B → C → D
```

Commit D still exists because another branch references it.

---

# Git Revert

## Purpose

`git revert` safely undoes a commit without rewriting history.

This is the preferred approach when working with shared repositories.

---

## Basic Syntax

```bash
git revert <commit-hash>
```

Example:

```bash
git revert a1b2c3d
```

---

## What Happens?

Before:

```text
A → B → C → D
```

Run:

```bash
git revert D
```

After:

```text
A → B → C → D → E
```

Where:

```text
E = commit that undoes D
```

The original commit remains in history.

---

## Why Revert Instead of Reset?

### Reset

```text
Deletes commits from branch history
```

### Revert

```text
Creates a new commit that reverses changes
```

History remains intact.

---

## Collaboration Example

Suppose three developers already have:

```text
A → B → C
```

If one developer runs:

```bash
git reset B
```

Their history becomes:

```text
A → B
```

While teammates still have:

```text
A → B → C
```

This can create synchronization problems.

Instead:

```bash
git revert C
```

Creates:

```text
A → B → C → D
```

where D safely reverses C.

Everyone can pull the new commit normally.

---

## Revert Can Cause Conflicts

Sometimes:

```bash
git revert <commit>
```

creates merge conflicts.

You may need to:

1. Open conflicted files
2. Resolve conflicts manually
3. Stage updates
4. Complete the revert commit

Example:

```bash
git add .
```

followed by the revert completion process.

---

# Comparison: Restore vs Reset vs Revert

| Command | Changes Files | Removes Commits | Moves Branch Pointer | Safe for Shared Repos |
|-----------|--------------|----------------|---------------------|----------------------|
| git restore | Yes | No | No | Yes |
| git reset | Yes | Yes | Yes | Usually No |
| git reset --hard | Yes | Yes | Yes | Dangerous |
| git revert | Yes | No | No | Yes |

---

# Quick Decision Guide

### Restore

Use when:

- You want a file back
- You want to discard local edits

```bash
git restore file.txt
```

---

### Reset

Use when:

- Commits are local only
- You want to rewrite history
- You want to move work to another branch

```bash
git reset HEAD~2
```

---

### Reset Hard

Use when:

- You are absolutely sure
- You want to delete commits and local work

```bash
git reset --hard HEAD~2
```

---

### Revert

Use when:

- Commit has already been shared
- Team members already pulled it
- You need a safe undo operation

```bash
git revert HEAD
```

---

# Final Mental Model

```text
RESTORE = Change my files.

RESET = Change my history, keep my work.

RESET --HARD = Change my history and delete my work.

REVERT = Preserve history and create an undo commit.
```

These four concepts form the foundation of Git recovery and undo operations.
