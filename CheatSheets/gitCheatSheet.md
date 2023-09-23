---
title: My Git Cheat Sheet
---

* TOC
{:toc}
## How to show a pretty history log?

### Log with date / time
`git log --pretty=format:"%h%x09%an%x09%ad%x09%s"`

with color
`git log --pretty="%C(Yellow)%h  %C(reset)%ad (%C(Green)%cr%C(reset))%x09 %C(Cyan)%an: %C(reset)%s"`

Make alias:

`git config --global alias.lg "log --color --graph --pretty=format:'%C(Yellow)%h  %C(reset)%ad (%C(Green)%cr%C(reset))%x09 %C(Cyan)%an: %C(reset)%s'"`

To remove the alias:
`git config --global --unset alias.lg`

## Commits

### How to commit a message only when there are no local changes. 

This comes in handy to avoid dummy commits.

`git commit --allow-empty --only -m <a message>`

## How to undo/revert things?

If a file has both staged and unstaged changes, only the unstaged changes shown in git diff are reverted. Changes shown in git diff --staged stay intact.

Source: [Stackoverflow](https://stackoverflow.com/questions/52704/how-do-i-discard-unstaged-changes-in-git#:~:text=If%20a%20file%20has%20both,diff%20%2D%2Dstaged%20stay%20intact.&text=Before%20Git%202.23-,For%20all%20unstaged%20files%20in%20current%20working,git%20checkout%20%2D%2D%20.)

### Revert unstaged files

#### Undo/Revert local changes of one unstaged file

`git restore <path to file>`

### Undo/Revert all local unstaged files

`git restore .`

### Remove untracked files

Use -n for a dry (test) run:
`git clean -nfd`

Actual delete:

`git clean -fd`

### Undo committed but unpushed

Delete the most recent commit, **destroying the work** you've done

`git reset --hard HEAD~1 `

Source: [Stackoverflow](https://stackoverflow.com/questions/3197413/how-do-i-delete-unpushed-git-commits)

## Merging

### Merging without commit 'and' without 'fast forward'

This is convenient to be able to inspect everything before the commit
`git merge <thebranchname> --no-commit --no-ff`

### Merging a branch into master using squash (without commit)

From master:
`git merge --squash feature/PBI_xxxx`

This also merge the changes without commit so that it can be inspected and manually committed in one commit

### Merging master into branch by favouring the master's changes (theirs) in case of conflict

`git merge --no-commit --no-ff --strategy-option theirs`

The command will report on what has automatically been resolved in case of conflict.

See [Git man](https://gitirc.eu/git-merge.html) for info about option `--strategy-option theirs`

`--no-commit --no-ff` has also been added to inspect the possible automatic conflicts before committing.

### How to abort an uncommitted merge

`git merge --abort`

# Rename a branch

1. Start by switching to the local branch which you want to rename:

`git checkout <old_name>`

2. Rename the local branch by typing:

`git branch -m <new_name>`

At this point, you have renamed the local branch.
If you’ve already pushed the <old_name> branch to the remote repository, perform the next steps to rename the remote branch.

3. Push the <new_name> local branch and reset the upstream branch:
`git push origin -u <new_name>`

4. Delete the <old_name> remote branch:

`git push origin --delete <old_name>`

Source: [Stackoverflow](https://stackoverflow.com/questions/30590083/how-do-i-rename-both-a-git-local-and-remote-branch-name)

## Inspecting branches

Small Gui tool to display the branches:
`gitk`

or full command line
`git log --graph --decorate --pretty=oneline --all --abbrev-commit`

To create an alias for this long command. For example `git lol` , you can type this (You have to type this only once!!):
`git config --global alias.lol "log --graph --decorate --pretty=oneline --all --abbrev-commit`

## Deleting branches

### Deleting a **local** branch

`git branch -d <branch-name>` 

_Note: Be careful with git branch -d, the branch will deleted and there is no way back.

### Deleting a **remote** branch

`git push origin --delete <branch-name>`

## Tags

### Push a single tag to remote

`git push origin <tag_name>`

### Fetch all remote tags

`git fetch --all`

### Delete local tag

`git tag -d <tag name>`

### Delete a remote tag

`git push --delete origin <tagname>`

### Push all tags to remote

`git push --tags`
