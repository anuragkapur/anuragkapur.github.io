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

## Correct commit message after pushing to remote
```shell
git rebase -i HEAD~n
git push --force
# Ref: https://help.github.com/articles/changing-a-commit-message/
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
