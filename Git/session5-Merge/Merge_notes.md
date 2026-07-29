# What is Git Merge?

Git Merge is used to combine changes from one branch into another branch.

### Think of it like this:

### School Project Example

Imagine two students are working on the same project:

``` Text
Ravi works on the Introduction section.
Priya works on the Conclusion section.
```

They create their own copies of the project to work independently.

In Git, these copies are called branches.

After finishing their work, they need to combine everything into the main project.

This process of combining changes is called Merge.

### What is a Branch?

A branch is simply a separate line of development.

``` text
main
 |
 ├── Branch-A (Ravi's work)
 |
 └── Branch-B (Priya's work)
```

Each person can work without affecting others.

Example of Merge

``` Text
Initially:

main
  |
  A
```

**Create a new branch:**

``` text
main
  |
  A
   \
    B (feature branch)
```

More work is done:

``` Text
main:    A --- C
           \
feature:    B --- D
```

Now we want all the work from feature branch in main.

We merge it:

``` Text
main: A --- C ------- M
         \          /
feature:  B --- D --
```

M = Merge Commit

Commands Used

**Step 1:** Go to main branch
```
git checkout main

or

git switch main
```

**Step 2:** Merge another branch
```
git merge feature
```

This means:

"Take all changes from the feature branch and add them into main."

Before Merge

Suppose:

``` Git
main branch
print("Hello")

feature branch
print("Hello")
print("Welcome")
```

After merge:

``` Git 
print("Hello")
print("Welcome")
```

Both changes are now in main.

**Types of Merge**

**1. Fast-Forward Merge**

When the main branch has not changed after creating the new branch.

Before:
``` Git
A --- B (main)
        \
         C --- D (feature)
```

After merge:

``` Git

A --- B --- C --- D (main)

```

Git simply moves the pointer forward.

**2. Three-Way Merge**

When both branches have new work.

Before:
``` Git
       C (main)
      /
A --- B
      \
       D (feature)
```

After merge:

``` Git
       C
      / \
A --- B   M
      \ /
       D
```

Git creates a special merge commit M.

**What is a Merge Conflict?**

Sometimes two people change the same line of a file.

``` Git
main branch
name = "Ravi"

feature branch
name = "Priya"

```

Git doesn't know which change is correct.

This creates a merge conflict.

Conflict Example

``` Git
Git shows:

<<<<<<< HEAD
name = "Ravi"
=======
name = "Priya"
>>>>>>> feature

```

You must manually choose:

``` Git
name = "Ravi and Priya"
```

``` Git
Then:
git add .
git commit
```

Conflict resolved!

Real Life Analogy

Think of branches as different roads.

``` Git
           Road A
          /
Start ----
          \
           Road B

```

People travel on different roads and later return to one main road.

Bringing both roads together is Git Merge.

Why Use Git Merge?

✅ Combine team members' work

✅ Keep main code updated

✅ Develop features separately

✅ Avoid disturbing existing code

✅ Essential for teamwork

### Quick Summary

Branch = Separate workspace.
Merge = Combine one branch into another.

``` Git
Command:
git merge branch-name
```
- Git automatically merges most changes.
- If the same line is changed in both branches, a merge conflict occurs.
- After resolving conflicts, commit the changes.
  
**One-Line Definition**

Git Merge is the process of combining changes from one branch into another branch so that all work becomes part of a single project. 🚀
