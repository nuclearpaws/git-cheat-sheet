# Git Cheat Sheet

## Intro

A handy git bash cheat sheet...

## Contents

1) [Setup](#Setup)
1) [Cloning](#Cloning)
1) [Branching](#Branching)
1) [Commiting](#Commiting)
1) [Keeping up to date](#Keeping-up-to-date)
1) [Resetting Repostiory](#Resetting-Repository)
1) [Sub Modules](#Sub-Modules)
1) [Change Logs](#Change-Logs)
1) [Tagging](#Tagging)

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
git push --set-upstream origin <origin name>
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

## Change Logs

### Standard:
```
git log
```

### GUI:
```
gitk
```

### Options:

> Log of commits on current branch by "nuclearpaws" since 2 weeks ago:

```
git log --since="two weeks ago" --author="nuclearpaws"
```

> Log of last 10 commits on current branch:
```
git log -10
```

> Commits across all branches:
```
git log --all
```

> Note you can combine those!

> Also note that `git log` and `gitk` are interchangable for most options.

> If after running this (or in any other case) the terminal prefix cursor is `:` rather then `$` it means there is more to display. You can press the `Enter` key to get another line or the `Page Down` key to get your height more lines printed. To stop printing more you can exit by pressing `q`.

### Making it console pretty:
```
git log --decorate --oneline --graph
```

> Once again, note all this can be combined!

```
git log --since="two weeks ago" --author="nuclearpaws" --all --decorate --oneline --graph
```

^ [Back to top](#Git-Cheat-Sheet)

---

## Tagging

### Listing Tags:
```
git tag -l
```

### Creating Tags:
```
git tag -a <tag> -m <description>
```

### Get Details about Tag:
```
git show <tag>
```

### Retro Taggins:
```
git tag -a <tag> <commit hash>
```

### Storing Tags:
> By default tags are only stored locally, and not transfered to remote with a `push`. In order to share the tags with the remote, use:

```
git push origin --tags
```
> Note that now anyone pulling from remote will get the tags too.

### Deleting Tags:
```
git tag -d <tag>
```

> Note this only deletes tags locally. To delete on remote use:

```
git push origin --delete <tag>
```

### Checking out Tags:
```
git checkout <tag>
```

^ [Back to top](#Git-Cheat-Sheet)

---