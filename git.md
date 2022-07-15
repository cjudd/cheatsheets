# GIT Cheat Sheet
By Christopher M. Judd (javajudd@gmail.com)

## Resources
* http://git-scm.com/book/en
* http://java.dzone.com/articles/some-notes-git
* http://gitolite.com/gitolite/sts.html
* http://gitimmersion.com/
* http://training.github.com/presentations/git-foundations.html#/
* http://nvie.com/posts/a-successful-git-branching-model/
* https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow
* https://spin.atomicobject.com/2016/06/26/parallelize-development-git-worktrees/
* https://dev.to/yankee/practical-guide-to-git-worktree-58o0

## create respository

### create new local repo
```
git init <project>
```

### clone existing repository
```
git clone <repo url>
```

## observer repo
### list new or modified files not committed
```
git status
```

### show changes to file not staged
```
git diff
```

### show changes to staged files
```
git diff --cached
```

### show all staged and unstaged file changes
```
git diff HEAD
```

### show changes between two commit ids
```
git diff <commit id 1> <commit id 2>
```

### list the change dates and authors for file
```
git blame <file>
```

### show file changes for commit id and/or file
```
git show <commit id>:<file>
```

## branches
### list all local branches
```
git branch
```

### list local and remote branches
```
git branch -av
```

### switch branch
```
git switch <branch>
git checkout <branch>
```

## checkout remote branch
```
git switch <branch>
git checkout -t origin/<feature>/<feature num>
git checkout -t origin/feature/<feature num>
```

## push remote branch
```
git push origin feature/<feature num>
git push -u origin feature/<feature num>
```

## list branches
```
git branch
git branch -v
git branch -r
```

## create branch
```
git branch <branch>
```

## delete/remove local branch
```
git branch -D feature/test
```

## delete/remove remote branch
```
git push origin --delete develop
```

## rename branch
```
git branch -m <oldname> <newname>
```

## list tags
```
git tag
```

## create tags
```
git tag -a <tag name> -m '<label>'
```

## push tags
```
git push --tags
```

## delete tags
```
git tag -d <tag>
git push origin :refs/tags/<tag>
```

## create branch from tag
```
git checkout -b <new branch name> <tag>
```

## synchronize
### get latest changes from origin
```
git fetch
```

### fetch latest changes from origin and merge
```
git pull
```

### fetch latest changes from origin and rebase
```
git pull --rebase
```

## merge
```
git merge <branch>
git merge --no-ff <branch>
```

## diff workspace
```
git diff
git diff <file>
```

## diff staged
```
git diff --cached
git diff --staged
```

## reset
```
git reset --hard origin/master
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

## rebase
```
git rebase <branch>
```

## diff branches
```
git diff --staged
git diff --name-status master..<branch>
```

## log 
```
git reflog -10
git log --oneline -10
git log --pretty=oneline
log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
git log -p <file/directory>
```

## log with file names
```
git log --stat
```

## stash 
### stashing
```
git stash
```
```
git stash save "<name>"
git stash list
git stash pop
git stash apply <stash name>
git stash apply stash@{2}
git stash drop <stash name>
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

## set origin url
```
git remote add origin http://<server>/<repo>.git
git remote rm <name>
```

## show origin url
```
git remote -v
git remote show origin
git config --get remote.origin.url
```

## remove origin
```
git remote rm origin
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

# copy or move full git repository
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