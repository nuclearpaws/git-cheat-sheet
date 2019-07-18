# Git Cheat Sheet

## Intro

This is a small git bash cheat sheet I've been working on just to keep myself from googling things when I was starting out. Now it seems to have grown into a full on guide tho. Oh well...

---

## Contents

1) [Setup](#Setup)
1) [Cloning](#Cloning)
1) [Branching](#Branching)
1) [Commiting](#Commiting)
1) [Keeping up to date](#Keeping-up-to-date)
1) [Undo, Rollback and Reset](#Undo-Rollback-and-Reset)
1) [Stashing Changes](#Stashing-Changes)
1) [Sub Modules](#Sub-Modules)
1) [Change Logs](#Change-Logs)
1) [Tagging](#Tagging)
1) [Aliases](#Aliases)
1) [Maintenance](#Maintenance)
1) [Cross Repo Merges](#Cross-Repository-Merges)
1) [Other Tips](#Other-Tips)

---

## Setup

### Set Up User Email (This is NOT Credentails):
```
git config --global user.email "<email>"
```
> This email is displayed under commits, when you push them to origin. This property MUST be set for git to work.

### Set Up UserName (This is NOT Credentials):
```
git config --global user.name "<name>"
```
> This name is displayed under commits, when you push them to origin. This property MUST be set for git to work.

### Set Up Credentail Manager):
```
get config --global credential.helper wincred
```
> This is where credentials are going to be stored. `WinCred` is the default Windows Credentails Manager. Open START and search for `Credential Manager`.

### Unsetting Config:
```
git config --global --unset <config to unset>
```

^ [Back to top](#Git-Cheat-Sheet)

---

## Cloning

### Clone:
```
git clone <git file url>
```
> **Notice:** you can get the `git file url` from where your git is hosted. Usually there is a `Clone` button that reveals the url.

### Clone with Sub-Modules:
```
git clone --recursive <git file url>
```
> **Notice:** this does not work with jusr `-r`!

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
git branch --delete <name>
```
> **Notice:** `-d` can be used instead of `--delete`.

> **Notice:** that you can do `-D` as well. The difference being that the `-d` will fail if there are un-pushed commits, meanwhile `-D` will delete the branch no matter what.

### List Local Branches:
```
git branch
```

### List Remote Branches:
```
git branch --remote
```
> **Notice:** you can use `-r` instead of `--remote`.

### List Remote and Local Branches:
```
git branch --all
```
> **Notice:** you can use `-a` instead of `--all`.

### Search Branches:
```
git branch --list "<pattern to find>"
```
> **Notice:** And example of the pattern would be `feature/*` or `*123*`

> **Notice:** this can also be combined with `--remote` to just search remote branches. etc.

### Renaming a Branch:
```
git branch --move <new name>
```
> **Notice:** this renames your current branch.

### Delete Remote Branch:
```
git push origin --delete <branch name>
```
> **Warning:** this is potentially dangerous as recovery may be impossible.

^ [Back to top](#Git-Cheat-Sheet)

---

## Commiting

### Stage File:
```
git add <file>
```

### Stage All Files:
```
git add .
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

## Undo, Rollback and Reset

### Roll back all file changes:
```
git reset --hard
```

### Delete all untracked files:
```
git clean -fdx
```

### Undo commits (keep changes/uncommit):
```
git reset --soft HEAD~<commit count>
```

### Undo commits (discard changes/delete commit):
```
git reset --hard HEAD~<commit count>
```
> **Notice:** that if the commit is already pushed to remote, your local branch will "diverge" from master. This can be fixed by overwriting a commit with a forced push.

### Forcing a Push (this can overwrite commits on remote):
```
git push --force
```
> As with many parameters, you can just use `-f` instead of `--force`. 

> **Notice:** this can be a very dangerous command to execute! Always make sure your branch is up to date with remote before you push your work this way.

### Reset local branch to the remote repository state
While on `<target branch>`
```
git fetch origin
git reset --hard origin/<target branch>
```
It is also advisible to [delete all untracked files](#delete-all-untracked-files) afterwards.
### Reset a file to another state:
```
git checkout <target branch> -- <path to the file>
```
> This is handy if you accidentally commit changes to config files.

> Do note the space between `--`.

^ [Back to top](#Git-Cheat-Sheet)

---

## Stashing Changes

> When you have some uncommited changes on your branch, and you dont want to commit them, but you have to switch branches, git stash may be for you. This is also useful if you accidentally started doing work on the wrong branch and cannot change it now due to uncommited changes.

### Storing the Changes:
> The quickest and easiest way is to just use:
```
git stash
```
> **Notice:** this will push all your tracked file changes to the stash and reset your current work environment back to whatever the branch head is poining at.

> Alternatively you can use:
```
git stash save <message>
```
> The Message is optional and represents a commit message like attribute to make identification of the stash easier, should you have many to keep track of.

> **Notice:** if the message is not provided, it gets automatically generated based on changes mage. This automatically generated message tends to be descriptive enough to keep track of different stashes.

If you want to stash untracked files use:
```
git stash --include-untracked
```
alternativley if you want to also stash all *git ignored* files use:
```
git stash --all
```


### Managing Stashes:
> You can view all stashes with:
```
git stash list
```

> You can delete a stash with:
```
git stash drop <id>
```
> Where the `<id>` is the "ID" of the stash you want to delete.

> You can also clear all stashes out with:
```
got stash clear
```
> **Warning:** this will delete **ALL** stashes!

### Applying the Changes:
> To apply stashed changes to your branch use:
```
git stash pop <id>
```
> **Notice:** that the `<id>` is optional, and what it represents is the "ID" of the stash. You can see all stash IDs when you view all stashes. It tends to be that its the stack order of the stashes, where 0 is your most recent one, increasting as your stashes get older.

> **(Notice:** you can also apply the stashed changes and keep the stash for later use again with:
```
git stash apply <id>
```
> Note that the `<id>` is once again optional.

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

> **Notice:** you can combine those!

> **Notice:** that `git log` and `gitk` are interchangable for most options.

> If after running this (or in any other case) the terminal prefix cursor is `:` rather then `$` it means there is more to display. You can press the `Enter` key to get another line or the `Page Down` key to get your height more lines printed. To stop printing more you can exit by pressing `q`.

### Making it console pretty:
```
git log --decorate --oneline --graph
```

> **Notice:** consider that all this can be combined like so:

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
> **Notice:** that tags can be listed in nicer ways, just like logs.
```
git log --tags --simplify-by-decoration --pretty="format:%ai -%d"
```
> For example, the above command will list tags with their creation date.

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
> **Notice:** by default tags are only stored locally, and not transfered to remote with a `push`. In order to share the tags with the remote, use:

```
git push origin --tags
```
> **Notice:** that now anyone pulling from remote will get the tags too.

### Deleting Tags:
```
git tag -d <tag>
```
> **Notice:** this only deletes tags locally. To delete on remote use:

```
git push origin --delete <tag>
```

### Checking out Tags:
```
git checkout <tag>
```

^ [Back to top](#Git-Cheat-Sheet)

---

## Aliases

### Add Alias:
```
git --global alias.<alias> <git command>
```
> **Notice:** the git aliases must be git commands. No standard CMD commands allowed.

### Use Alias:
```
git <alias>
```

### Remove Alias:
```
git --global --unset alias.<alias>
```
> **Notice:** this is just like unsetting git config/settings.

^ [Back to top](#Git-Cheat-Sheet)

--- 

## Maintenance

### Prune Upstreams:
```
git prune
```

### Prune References to Origin:
```
git fetch --prune origin
```
> **Notice:** you can just use `-p` instead of `--prune`.

### General House Keeping:
```
git gc
```

^ [Back to top](#Git-Cheat-Sheet)

--- 

## Cross Repository Merges
> As odd as it may be, there is sometimes a need to merge two repositories. This is usually when something you have forked off has been updated and you require said update in your fork of it.

> Do note that this is best done with forked repositories, however there is nothing stopping you from merging two completely separate repositories too. Thing may just get really messy.

> I also recommend doing this on a seperate clone of the two repos as I believe once you merge the two repositories in this way, they will staty this way unless detached.

### Make New Merge Environment:
```cmd
mkdir CROSS_REPO_MERGE
cd CROSS_REPO_MERGE
git clone <TargetRepo>.git
git clone <SourceRepo>.git
cd TargetRepo
```
> **Notice:** this part is OS Specific. This example is made in Windows.

### Set Environment to Reference Both Repos:
```
git remote add SOURCE ../<SourceRepo>/.git
git fetch SOURCE
git branch SOURCE RepoMergeBranch
```

### Merge Source into Target:
```
git merge <TargetBranch>
git merge SOURCE/<SourceBranch>
```

### Commit and Push Merge:
```
git add .
git commit -m "Merged <SourceRepo>/<SourceBranch> into <TargetRepo>/<TargetBranch>"
git push
```

> References for this part:
>- [Merge difference code changes from one repository branch to another repository branch](https://stackoverflow.com/questions/21376489/merge-difference-code-changes-from-one-repository-branch-to-another-repository-b)
>- [How to combine two branches from two different repositories in a single repository?](https://stackoverflow.com/questions/244695/how-to-combine-two-branches-from-two-different-repositories-in-a-single-reposito)

^ [Back to top](#Git-Cheat-Sheet)

--- 

## Other Tips

### Logging Recent Git Commands:
```
git reflog
```

### Show Git Bash History:
``` cmd
history
```
> **Notice:** this may be OS Specific. Example is in Windows.


^ [Back to top](#Git-Cheat-Sheet)

--- 
