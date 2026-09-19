# Comprehensive Guide to `git diff`

`git diff` is a core Git command used to inspect changes between commits, commit history, working directories, and the staging area (index).

---

## 1. Understanding Git's Three States

To understand `git diff`, you need to know Git's three main areas:
1. **Working Directory:** Files currently being modified on your local machine.
2. **Staging Area (Index):** Files marked with `git add` to be included in the next commit.
3. **Repository (HEAD):** The state of your files at your most recent commit.

```
Working Directory  ──( git add )──>  Staging Area  ──( git commit )──>  Repository (HEAD)
```

---

## 2. Anatomy of `git diff` Output

When you run `git diff`, Git outputs a unified diff format. Here is how to read it:

```diff
diff --git a/app.py b/app.py
index e69de29..496d649 100644
--- a/app.py
+++ b/app.py
@@ -1,3 +1,4 @@
 def main():
-    print("Hello")
+    print("Hello, World!")
+    print("Welcome to Git")
```

### Breakdown:
- `--- a/app.py`: The original version of the file (before changes).
- `+++ b/app.py`: The new version of the file (after changes).
- `@@ -1,3 +1,4 @@`: The "chunk header" (or hunk).
  - `-1,3`: In the original file, chunk starts at line `1` and spans `3` lines.
  - `+1,4`: In the new file, chunk starts at line `1` and spans `4` lines.
- `- print("Hello")`: A line that was removed.
- `+ print("Hello, World!")`: A line that was added.
- Unmarked lines: Context lines that remained unchanged.

---

## 3. The Main Types of `git diff` (With Examples)

Here are the primary ways `git diff` is used, categorized by what they compare:

---

### Type 1: Working Directory vs. Staging Area (Unstaged Changes)
Shows changes you have made in your files that have **not** yet been staged with `git add`.

#### Command:
```bash
git diff
```

#### Specific File:
```bash
git diff path/to/file.txt
```

#### Example Scenario:
You edit `main.py`, adding a new function, but haven't run `git add main.py`. Running `git diff` displays the lines added or deleted since the last stage or commit.

---

### Type 2: Staging Area vs. Repository (Staged Changes)
Shows changes you have staged with `git add` that are waiting to be committed, compared against your last commit (`HEAD`).

#### Command:
```bash
git diff --staged
# or (synonym)
git diff --cached
```

#### Specific File:
```bash
git diff --staged path/to/file.txt
```

#### Example Scenario:
You ran `git add .` and want to review what will go into your commit before typing `git commit`.

---

### Type 3: Working Directory vs. Repository (All Uncommitted Changes)
Shows both staged and unstaged modifications compared directly to your last commit (`HEAD`).

#### Command:
```bash
git diff HEAD
```

#### Specific File:
```bash
git diff HEAD path/to/file.txt
```

#### Example Scenario:
You staged some files and modified others without staging. `git diff HEAD` shows everything that differs from your last commit.

---

### Type 4: Between Two Commits
Compares the state of the project between two specific points in history using commit hashes, branch names, or tags.

#### Command:
```bash
git diff <commit-A> <commit-B>
```

#### Example:
```bash
git diff 1a2b3c4 5d6e7f8
```
*Note: This compares the state at `<commit-A>` directly to `<commit-B>`.*

---

### Type 5: Between Two Branches
Compares two branches to see how their tips differ.

#### Command (Two-Dot Diff):
```bash
git diff branch1..branch2
# Or simply:
git diff branch1 branch2
```
* Compares the tip of `branch1` directly to the tip of `branch2`.

#### Command (Three-Dot Diff):
```bash
git diff branch1...branch2
```
* Compares `branch2` against the **common ancestor** (merge-base) of `branch1` and `branch2`.
* *Tip:* This is the exact diff shown when opening a Pull Request / Merge Request on GitHub or GitLab.

---

### Type 6: Between Working Directory and a Remote Branch
Shows how your current local files differ from an upstream remote branch.

#### Command:
```bash
git fetch origin
git diff origin/main
```

---

## 4. Useful Flags and Modifiers

| Flag | Purpose | Example |
| :--- | :--- | :--- |
| `--stat` | Shows a summary of files changed, additions, and deletions | `git diff --stat` |
| `--name-only` | Lists only the names of modified files | `git diff --name-only main..feature` |
| `--name-status` | Lists changed files along with their status (`M`, `A`, `D`) | `git diff --name-status` |
| `-w` or `--ignore-all-space` | Ignores whitespace differences | `git diff -w` |
| `--word-diff` | Highlights changes inline word-by-word instead of line-by-line | `git diff --word-diff` |
| `--compact-summary` | Condensed summary of changed files and line counts | `git diff --compact-summary` |

---

## 5. Quick Reference Cheat Sheet

```bash
# 1. Unstaged changes (Working Tree vs Index)
git diff

# 2. Staged changes (Index vs HEAD)
git diff --staged

# 3. All uncommitted changes (Working Tree vs HEAD)
git diff HEAD

# 4. Changes in a specific file
git diff path/to/file

# 5. Differences between two commits
git diff commit1 commit2

# 6. Differences between two branches
git diff main feature-branch

# 7. Differences since common ancestor (Pull Request view)
git diff main...feature-branch

# 8. High-level summary of changes
git diff --stat
```