# 🌿 Git Branching Notes

A colorful README with explanations, diagrams, and Git commands.

![Git](https://img.shields.io/badge/Git-Branching-orange?style=for-the-badge&logo=git)
![Version Control](https://img.shields.io/badge/Version-Control-blue?style=for-the-badge)

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

