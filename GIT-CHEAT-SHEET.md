# Git Cheat Sheet

## Intro

A handy git bash cheat sheet...

## Contents

1) [Setup](##Setup)
1) [Cloning](##Cloning)
1) [Branching](##Branching)
1) [Commiting](##Commiting)
1) [Keeping up to date](##Keeping-up-to-date)
1) [Resetting Repostiory](##Resetting-Repository)
1) [Sub Modules](##Sub-Modules)

---

## Setup

### Set Up User Email (not credentails):
```
git config --global user.email "<email>"
```

### Set Up UserName (not credentials):
```
git config --global user.name "<name>"
```

### Set Up Credentail Manager:
```
get config --global credential.helper wincred
```

^ [Back to top](#Git-Cheat-Sheet)

---

## Cloning

### Clone:
```
git clone <git file url>
```

### Clone with Sub-Modules:
```
git clone --recursive <git file url>
```

^ [Back to top](#Git-Cheat-Sheet)

---

## Branching

### Create New Local Branch:
```
git checkout -b <name>
```

### Create New Local Branch with Upstream:
```
git checkout -b <name> <origin name>
```

### Set Upstream for Local Branch:
```
git push origin <origin name>
```

### Checkout Branch:
```
git checkout <name>
```

### Delete Local Branch:
```
git branch -D <name>
```

### List Local Branches:
```
git branch
```

### List Remote Branches:
```
git branch -r
```

### List Remote and Local Branches:
```
git branch -a
```

^ [Back to top](#Git-Cheat-Sheet)

---

## Commiting

### Stage:
```
git add <file>
```

### Unstage:
```
git reset HEAD <file>
```

### Commit:
```
git commit -m "<message>"
```

### Push:
```
git push
```

^ [Back to top](#Git-Cheat-Sheet)

---

## Keeping up to date

## Update Branch Info:
```
git fetch
```

## Update Current Branch from Remote:
```
git pull
```

## Merge Branch into your Branch:
```
git merge <name of branch to merge into current branch>
```

^ [Back to top](#Git-Cheat-Sheet)

---

## Resetting Repository

### Roll back file changes:
```
git reset --hard
```

### Delete all untracked files:
```
git clean -fdx
```

### Undo commits (keep changes):
```
git reset --soft HEAD~<commit count>
```

### Undo commits (discard changes):
```
git reset --hard HEAD~<commit count>
```

^ [Back to top](#Git-Cheat-Sheet)

---

## Sub-Modules

### Update:
```
git submodule update --init
```

### Update with nested submodules:
```
git submodule update --init --recursive
```

^ [Back to top](#Git-Cheat-Sheet)

---
