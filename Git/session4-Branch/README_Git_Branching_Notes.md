# 🌿 Git Branching Notes

A colorful README with explanations, diagrams, and Git commands.

![Git](https://img.shields.io/badge/Git-Branching-orange?style=for-the-badge&logo=git)
![Version Control](https://img.shields.io/badge/Version-Control-blue?style=for-the-badge)
![Git](https://img.shields.io/badge/Git-delete-Branching-yellow?style=for-the-badge&logo=git)

---
## What is Git Branch?
### Imagine a Tree 🌳

A tree has:

**One main trunk** → This is the **Main Branch** (main or master)
**Many smaller branches** growing from it → These are **Git Branches**

Just like tree branches let new leaves grow without changing the trunk, Git branches let you work on new changes without affecting the main project.

Branches are alternative timelines that allow isolated development.

---
### Why Use Branches? 🤔

✅ Multiple people can work at the same time.<br>
✅ Mistakes Won't damage the main project.<br>
✅ New Features can be tested safely.<br>
✅ Easy to organize work.

#### Simple example:

#### Main Branch
   
The teacher keeps the final project in a folder called:
   
```text
main
```
#### Real-Life GitHub Example

Let's say a website project has:

```text
main
```

A developer creates:
```text
login-feature
```
Another developer creates:
```text
dark-mode
```
Structure:
```text
main
 ├── login-feature
 └── dark-mode
```

Each person works separately.

When everything works correctly, their changes are merged back into main.

---
## Commands

```bash
git branch new-feature
git switch new-feature

```
The git branch command does more than just create and delete branches. If you run it with no arguments, you get a simple listing of your current branches:
```text
$ git branch
  iss53
* master
  testing
```
---

### Example: Branch excercise 

Here are the Git commands for the exercise, along with a description of what each command does.

#### 1. Create the project folder and initialize Git
```text
mkdir Patronus
cd Patronus
git init
```

#### Description:
- mkdir Patronus → Creates a new directory named Patronus.
- cd Patronus → Moves into the new directory.
- git init → Creates a new Git repository in the current folder.

#### 2. Create and commit the empty file
```text
touch patronus.txt
git add patronus.txt
git commit -m "add empty patronus file"
```

#### Description:
- touch patronus.txt → Creates an empty file.
- git add patronus.txt → Stages the file for commit.
- git commit -m "add empty patronus file" → Saves the file in Git history.

#### 3. Create the harry and snape branches
```text
git branch harry
git branch snape
```

#### Description:
- Creates two new branches (harry and snape) from the current branch (typically master or main).
- Does not switch to them.

#### 4. Switch to the harry branch using the "new" command
```text
git switch harry
```

#### Description:
- Moves your working directory to the harry branch.
- git switch is the newer, more intuitive command for changing branches.

#### 5. Add Harry's Patronus and commit

Edit patronus.txt, then save the Harry patronus ASCII art.
```text
git add patronus.txt
git commit -m "add harry's stag patronus"
```

#### Description:
- Stages the modified file.
- Creates a commit containing Harry's patronus.

#### 6. Move to the snape branch using the "older" command
```text
git checkout snape
```

#### Description:
- Switches from harry to snape.
- git checkout is the older command traditionally used for branch switching.

#### 7. Add Snape's Patronus and commit

Replace the contents of patronus.txt with Snape's patronus art.
```text
git add patronus.txt
git commit -m "add snape's doe patronus"
```

#### Description:
- Stages the changes.
- Creates a commit on the snape branch.

#### 8. Create the lily branch from snape
```text
git branch lily
```

#### Description:
- Creates a new branch named lily from the current branch (snape).

#### 9. Switch to the lily branch
```text
git switch lily
```

#### Description:
- Changes your current branch to lily.

#### 10. Update the title and commit

**Change:**

SNAPE'S PATRONUS

**to:**

LILY'S PATRONUS


**Then run:**
```text
git add patronus.txt
git commit -m "add lily's doe patronus"
```

#### Description:
- Stages the title change.
- Creates a new commit while keeping the same doe ASCII art.
  
#### 11. List all branches
```text
git branch
```

#### Description:

- Displays all local branches.
- You should see something similar to:
```text
harry
* lily
master
snape
```

(* indicates the current branch.)

#### 12. Bonus: Delete the snape branch

First switch away from snape if you're on it:
```text
git switch lily
```

Delete the branch:
```text
git branch -d snape
```

#### Description:
- Removes the local snape branch.
- Git safely deletes it only if its changes exist elsewhere.

* If Git warns that the branch is not fully merged, force deletion:
```text
git branch -D snape
```
Optional: Verify Branch History
```text
git log --oneline --graph --all --decorate
```

#### Description:

- Shows a visual representation of all branches and commits, helping you see the relationships between harry, snape, and lily.


