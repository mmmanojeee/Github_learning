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

---
### Why Use Branches? 🤔

✅ Multiple people can work at the same time.<br>
✅ Mistakes Won't damage the main project.<br>
✅ New Features can be tested safely.<br>
✅ Easy to organize work.

---
## What is a Branch?
Branches are alternative timelines that allow isolated development.

```text
A --> B --> C
           \
            D --> E
```

## Merge
```text
A --> B --> C -------- M
           \         /
            D --> E
```

## Commands
```bash
git branch new-feature
git switch new-feature
git merge new-feature
```

## Branching layout

```
redesign
                    |
                    F
                   /
A---B---C---D-----E
         \
          G---H
          bug-fix

         \
          I---J
          new-color-scheme

```
