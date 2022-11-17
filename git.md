# GIT Cheat Sheet
By Christopher M. Judd (javajudd@gmail.com)

## Resources
* http://git-scm.com/book/en
* http://java.dzone.com/articles/some-notes-git
* http://gitolite.com/gitolite/sts.html
* http://gitimmersion.com/
* https://tapajyoti-bose.medium.com/git-cheat-sheet-with-40-commands-concepts-ab1b9d973e96
* http://training.github.com/presentations/git-foundations.html#/
* http://nvie.com/posts/a-successful-git-branching-model/
* https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow
* https://spin.atomicobject.com/2016/06/26/parallelize-development-git-worktrees/
* https://dev.to/yankee/practical-guide-to-git-worktree-58o0

## Create Respository

### Initialize local repository
```
git init <directory>
```

### Clone existing remote repository
```
git clone <repo url>
```

## Add Files

### Add file to staging area
```
git add <file>
```

### Add all files to staging area
```
git add .
```

## Status

### List new or modified files not committed
```
git status
```

## Commit

### Commit changes to staged files
```
git commit -m "<message>"
```

### Add and commit changes
```
git commit -a -m "<message>"
git commit -am "<message>"
```

### Checkout a previous commit
```
git commit <commit id>
```

### Revert a commit
```
git revert <commit id>
```

### Reset a commit
```
git reset <commit id>
git reset --hard <commit id>
git reset --hard origin/master
```

## Restore

### Restore/discard changes in working directory
```
git restore <file>
```

### Restore/unstage changes in staging area
```
git restore --staged <file>
```

## Files

### Move or Rename file
```
git mv <current path> <new path>
```

### Remove a file from repo
```
git rm <file>
```

### Remove file from staging
```
git rm --cached <file>
```

## Branches

### List local branches
```
git branch
```

### List remote branches
```
git branch -r
```

### List local and remote branches
```
git branch -a
```

### List branches with last commit
```
git branch -v
```

### Create branch
```
git branch <branch>
```

### Create and switch branch
```
git checkout -b <branch>
```

### Switch branch
```
git switch <branch>
git checkout <branch>
```

### Delete/remove local branch
```
git branch -D <branch>
```

### Delete/remove remote branch
```
git push origin --delete <branch>
```

## Merge

### Merge branch
```
git merge <branch to merge into head>
```

### Merge No fast-forward
Creates a merge commit even if the merge resolves as a fast-forward.
```
git merge --no-ff <branch to merge into head>
```

### Merge squash
Squashes all commits from branch into a single commit.
```
git merge --squash <branch to merge into head>
```

## Rebase

### Rebase banch
```
git rebase <branch to rebase from>
```

## History

### Default commit history
```
git log
```

## Commit history with file names
```
git log --stat
```

### Commit history with diff
```
git log -p
```

### Hash (short) and comment limited
```
git log --oneline -10
```

### Hash (short) and comment limited to a # of commits
```
git log --oneline -10
```

### Hash (full) and comment
```
git log --pretty=oneline
```

### Hash (short), HEAD index and comment
```
git reflog -10
```

### Hash (short), date, comment, author
```
git log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
```

## Diff

### Show changes to unstaged files
```
git diff
```

### Show changes to staged files
```
git diff --staged
```

### Show changes between two commits
```
git diff <commit id 1> <commit id 2>
```

## Stash 

### Stashing
```
git stash
```

### Stashing with message
```
git stash save "<message>"
```

### List stash
```
git stash list
```

### Apply stash
```
git stash apply <id>
git stash apply stash@{<index>}
```

### Apply and remove (pop) stash
```
git stash pop
git stash pop <stash id>
```

### Display stash changes
```
git stash show <stash id>
```

### Remove stash
```
git stash drop <stash id>
```

### Remove all stashes
```
git stash clear
```

## Remote Repositories

### Add remote repository
```
git remote add <remote alias> <url>
git remote add origin <url>
```

### List remote repositories
```
git remote
git remote -v
git remote show <alias>
git config --get remote.origin.url
```

## Remove remote repository
```
git remote rm <remote alias>
```

## Rename remote repository
```
git remote rename <old alias> <new alias>
```

## Synchronize

### Fetch latest changes from origin
```
git fetch
```

### Fetch latest changes from remote repository
```
git fetch <remote alias>
```

### Fetch latest changes from remote repository's particular branch
```
git fetch <remote alias> <branch>
```

### Pull latest changes from origin
```
git pull
```

### Pull latest changes from remote repository and particular branch
```
git pull <remote alias> <branch>
```

### Pull latest changes from origin and rebase
```
git pull --rebase
```

## Push changes to remote repository
```
git push
git push <remote alias>
git push <remote alias> <branch>
```

## Tags

### List tags
```
git tag
```

### Create tags
```
git tag -a <tag name> -m '<label>'
```

### Push tags
```
git push --tags
```

### Delete tags
```
git tag -d <tag>
git push origin :refs/tags/<tag>
```

## Create branch from tag
```
git checkout -b <new branch name> <tag>
```


## Other

### checkout remote branch
```
git switch <branch>
git checkout -t origin/<feature>/<feature num>
git checkout -t origin/feature/<feature num>
```


### rename branch
```
git branch -m <oldname> <newname>
```

### list the change dates and authors for file
```
git blame <file>
```

### show file changes for commit id and/or file
```
git show <commit id>:<file>
```



## undo last commit
```
git reset --soft HEAD~
git reset HEAD
```

## amend (or add to previous commit)
```
git add .
git commit --amend
```

## ignore files (untrack files)
```
git update-index --assume-unchanged path/to/file
```

## retrack files (track files again)
```
git update-index --no-assume-unchanged path/to/file
```

## diff branches
```
git diff --staged
git diff --name-status master..<branch>
```

## create patch
```
git format-patch <parent branch>
```

## apply patch
```
git am < <patch file>
```

## bundles
```
git bundle create <repo>.bundle master
git clone <repo>.bundle -b master <bundle>
```

## show config
```
git config --list
```

## common configs
```
git config --global user.name "[name]"
git config --global user.email "[email address]"
git config --global color.ui auto
```

## revert to a specific commit
```
git reset ea5a181
git reset --soft <sha>
git commit -m "Revert to <sha>"
git reset --hard
git clean -f -d
git push -f origin <branch name>
```

## cherry pick
```
git cherry-pick <commit sha>
```

## list ignored files
```
git ls-files --other --ignored --exclude-standard
```

## contains commit
```
git branch --contains <sha>
git log -p <branch1> --not <branch2>
```

## show repositories
```
ssh git@<server> info
```
## Git Worktrees
## list trees
```
git worktree list
```

## add tree
```
git fetch
git branch <branch> origin/<branch>
git worktree add <tree dir> <branch>
```

### clean tree
```
git worktree remove <tree dir>
```

## GIT Flow
### list/start/finish feature branches
```
git flow feature
git flow feature start <name> [<base>]
git flow feature finish <name>
```

### push/pull a feature branch to the remote repository
```
git flow feature publish <name>
git flow feature pull <remote> <name>
git flow feature pull origin <name>
```

### list/start/finish release branches
```
git flow release
git flow release start <release> [<base>]
git flow release finish <release>
```

### list/start/finish hotfix branches
```
git flow hotfix
git flow hotfix start <release> [<base>]
git flow hotfix finish <release>
```

### list/start support branches
```
git flow support
git flow support start <release> <base>
```

## Copy/Move Repository
### copy or move full git repository
```
git clone --mirror <repo url> temp-dir
cd temp-dir
git tag
git branch -a
git remote rm origin
git remote add origin <new repo url>
git push origin --all
git push --tags
```

## Backup

### Backup up full repository
https://stackoverflow.com/questions/11792671/how-to-git-bundle-a-complete-repo
```
git clone --mirror git@example.org:path/repo.git
git bundle create repo.bundle --all
```