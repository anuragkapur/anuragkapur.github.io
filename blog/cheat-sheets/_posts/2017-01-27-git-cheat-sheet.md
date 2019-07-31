---
layout: post
title:  "GIT cheat sheet"
teaser: Cheat sheet for the GIT command line
date:   2017-01-27 12:09:26 +0000
categories: cheat-sheets
---

# Commits, reverts etc

## Revert committed changes to a single file
```shell
$ git checkout <revision number to revert to> <file path>
$ git commit
```

## Revert merge commit
```shell
git revert -m 1 [sha_of_merge_commit]
```

## Correct commit message that hasn't been pushed yet
```shell
git commit --amend
# Ref: https://help.github.com/articles/changing-a-commit-message/
```

## Rewrite history after pushing to remote
```shell
git rebase -i HEAD~n
git push --force
```
Ref:     
https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History        
https://help.github.com/articles/changing-a-commit-message/

## Force pull from remote
```shell
git fetch --all
git reset --hard origin/master
git pull origin master
```

## Git pull allowing unrelated histories
```shell
git pull --allow-unrelated-histories
```

# Branches

## Delete remote branch
```shell
$ git push origin --delete <branch-name>
```

## Rename local and remote branch
```shell
git branch -m old_branch_name new_branch_name
git push origin :old_branch_name
git push --set-upstream origin new_branch_name
```

# Tags

## Create tag
```shell
git tag v1.7.1
```

## Push tag to remote
```shell
git push origin v2.44.0
```

## Delete remote tag
```shell
git push --delete origin v1.7.1
```

## Delete local tag
```shell
git tag --delete v1.7.1
``` 

# Forks

## Update fork from origin
```shell
$ git remote add upstream <remote-repo-url>
$ git fetch upstream
$ git checkout master
$ git pull
$ git merge upstream/master
```

# Git submodules
## Init and update submodules
```shell
$ git submodule init
$ git submodule update
```
