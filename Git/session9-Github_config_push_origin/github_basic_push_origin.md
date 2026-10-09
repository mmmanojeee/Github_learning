# GitHub Complete Beginner Notes + Hands-On Lab

## Overview

These notes are designed for someone who is completely new to Git and GitHub. They explain the concepts from the transcript in simple language, include practical examples, and provide a complete hands-on lab.

---

# 1. What is GitHub?

GitHub is a cloud-based platform that hosts Git repositories.

Think of GitHub as:

> Google Drive for software projects, powered by Git.

GitHub allows developers to:

- Store code online
- Collaborate with others
- Track changes
- Review code
- Manage issues and bugs
- Automate deployments
- Contribute to open-source projects

---

# 2. Git vs GitHub

## Git

Git is a Version Control System (VCS).

Responsibilities:

- Track file changes
- Maintain history
- Create branches
- Merge work
- Work offline

Example:

```bash
git init
git add .
git commit -m "Initial Commit"
```

## GitHub

GitHub is a cloud service that stores Git repositories.

Example:

```bash
git push origin main
```

This uploads local commits to GitHub.

---

# 3. Why Use GitHub?

## Code Backup

If your laptop crashes, your code remains safe on GitHub.

## Collaboration

Multiple developers can work together on the same project.

## Open Source

Many famous projects are hosted on GitHub:

- React
- Kubernetes
- TensorFlow
- VS Code

## Portfolio Building

Recruiters often review GitHub profiles.

## Learning

You can explore real-world projects and understand industry practices.

---

# 4. GitHub Pricing

GitHub provides free plans that support:

- Unlimited public repositories
- Unlimited private repositories
- Collaboration
- Basic automation features

---

# 5. What is Cloning?

Cloning means copying an existing repository from a remote location to your local machine.

```bash
git clone https://github.com/user/project.git
```

Git downloads:

- Files
- Commit history
- Branch information

---

# 6. Public Repository Access

If a repository is public:

- Anyone can clone it
- Anyone can view it
- Not everyone can push changes

Only authorized users can push directly.

---

# 7. GitHub Account Setup

1. Visit https://github.com
2. Create account
3. Verify email
4. Configure Git

```bash
git config user.name "Your Name"
git config user.email "you@example.com"
```

---

# 8. SSH Authentication

SSH allows secure communication with GitHub.

Benefits:

- No repeated password entry
- More secure authentication

## Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "you@example.com"
```

## Check Existing Keys

```bash
ls ~/.ssh
```

Look for:

```text
id_ed25519
id_ed25519.pub
```

Upload the public key to GitHub.

---

# 9. Upload Existing Local Repository to GitHub

## Create Repository Locally

```bash
git init
```

## Create Remote Repository in GitHub

Create an empty repository.

## Connect Repository

```bash
git remote add origin https://github.com/user/project.git
```

---

# 10. What is a Remote?

A Remote is a reference to another repository location.

Example:

```bash
git remote add origin https://github.com/user/project.git
```

Here:

- origin = remote name
- URL = remote repository

Verify:

```bash
git remote -v
```

---

# 11. What is Push?

Push uploads commits from local repository to remote repository.

```bash
git push origin main
```

Explanation:

- git push → upload commits
- origin → destination remote
- main → branch name

Workflow:

```text
Modify Files
↓
git add
↓
git commit
↓
git push
```

---

# 12. Branches

Branches allow parallel development.

Example:

```text
main
feature-login
feature-dashboard
```

Create branch:

```bash
git checkout -b feature-login
```

Push branch:

```bash
git push origin feature-login
```

---

# 13. Main vs Master

Historically:

```text
master
```

Modern default branch:

```text
main
```

Rename branch:

```bash
git branch -M main
```

---

# 14. Upstream Tracking

```bash
git push -u origin main
```

This creates a tracking relationship.

After that:

```bash
git push
```

is sufficient.

---

# 15. Typical GitHub Workflow

```text
Clone Repository
Create Branch
Make Changes
Commit Changes
Push Branch
Create Pull Request
Merge Changes
```

---

# 16. Most Important Commands

## Clone

```bash
git clone URL
```

## Add Remote

```bash
git remote add origin URL
```

## Show Remotes

```bash
git remote -v
```

## Push

```bash
git push origin main
```

## Set Upstream

```bash
git push -u origin main
```

## Rename Branch

```bash
git branch -M main
```

---

# 17. Interview Questions

## Difference Between Git and GitHub?

Git:

- Version Control System
- Local tool

GitHub:

- Cloud platform
- Hosts Git repositories

## What Happens During Clone?

- Repository downloaded
- Commit history downloaded
- Remote origin configured

## What Is Remote?

A named reference to another repository.

## Why Use git push -u?

Creates tracking relationship.

## Can Anyone Clone a Public Repo?

Yes.

## Does Commit Automatically Update GitHub?

No.

You must run:

```bash
git push
```

---

# Hands-On Lab Exercise

## Objective

Practice:

- Repository creation
- GitHub integration
- Branching
- Pushing changes
- Merging branches
- Resolving conflicts

---

## Step 1: Create Local Repository

```bash
mkdir Favorites
cd Favorites
git init
```

Verify:

```bash
git status
```

---

## Step 2: Create GitHub Repository

Example:

```text
gh-favorites-exercise
```

Copy repository URL.

---

## Step 3: Connect Local Repository

```bash
git remote add origin https://github.com/username/gh-favorites-exercise.git
```

Verify:

```bash
git remote -v
```

---

## Step 4: Create File

```bash
touch favorites.txt
```

Commit:

```bash
git add favorites.txt
git commit -m "Add empty favorites file"
```

---

## Step 5: Rename to Main

```bash
git branch -M main
```

---

## Step 6: Push Main Branch

```bash
git push origin main
```

---

## Step 7: Create Branches

```bash
git branch foods
git branch movies
```

Verify:

```bash
git branch
```

---

## Step 8: Work on Foods Branch

```bash
git switch foods
```

Add:

```text
Pizza
Biryani
Ice Cream
```

Commit:

```bash
git add favorites.txt
git commit -m "Add favorite foods"
```

---

## Step 9: Work on Movies Branch

```bash
git switch movies
```

Add:

```text
Interstellar
Inception
Bahubali
```

Commit:

```bash
git add favorites.txt
git commit -m "Add favorite movies"
```

---

## Step 10: Push Foods Branch

```bash
git push origin foods
```

---

## Step 11: Push Movies Branch

```bash
git push origin movies
```

---

## Step 12: Merge Foods into Main

```bash
git switch main
git merge foods
```

---

## Step 13: Merge Movies into Main

```bash
git merge movies
```

Possible result:

```text
Merge Conflict
```

---

## Step 14: Resolve Merge Conflict

Conflict:

```text
<<<<<<< HEAD
Pizza
Biryani
Ice Cream
=======
Interstellar
Inception
Bahubali
>>>>>>> movies
```

Resolve:

```text
Pizza
Biryani
Ice Cream

Interstellar
Inception
Bahubali
```

---

## Step 15: Commit Merge Result

```bash
git add favorites.txt
git commit -m "Merge foods and movies"
```

---

## Step 16: Push Final Version

```bash
git push origin main
```

---

# Key Takeaways

✅ Git and GitHub are different

✅ Clone downloads repositories locally

✅ Remotes connect repositories

✅ Push uploads commits

✅ Branches isolate work

✅ Merge combines work

✅ Conflicts occur when multiple branches modify the same area

✅ GitHub is essential for modern software development and collaboration
