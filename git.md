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

## stashing
```
git stash
git stash save "<name>"
git stash list
git stash pop
git stash apply <stash name>
git stash apply stash@{2}
git stash drop <stash name>
```

## checkout remote branch
```
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

## delete/remove branch
```
git branch -D feature/test
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
```

## log with file names
```
git log --stat
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