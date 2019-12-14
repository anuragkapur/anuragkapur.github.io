---
layout: post
title:  "GIT cheat sheet"
teaser: Cheat sheet for the GIT command line
date:   2017-01-27 12:09:26 +0000
categories: cheat-sheets
tags: cheat-sheets
---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Commits, reverts etc](#commits-reverts-etc)
  - [Revert committed changes to a single file](#revert-committed-changes-to-a-single-file)
  - [Revert merge commit](#revert-merge-commit)
  - [Correct commit message that hasn't been pushed yet](#correct-commit-message-that-hasnt-been-pushed-yet)
  - [Rewrite history after pushing to remote](#rewrite-history-after-pushing-to-remote)
  - [Force pull from remote](#force-pull-from-remote)
  - [Git pull allowing unrelated histories](#git-pull-allowing-unrelated-histories)
- [Branches](#branches)
  - [Delete remote branch](#delete-remote-branch)
  - [Rename local and remote branch](#rename-local-and-remote-branch)
- [Tags](#tags)
  - [Create tag](#create-tag)
  - [Push tag to remote](#push-tag-to-remote)
  - [Delete remote tag](#delete-remote-tag)
  - [Delete local tag](#delete-local-tag)
- [Forks](#forks)
  - [Update fork from origin](#update-fork-from-origin)
- [Git submodules](#git-submodules)
  - [Init and update submodules](#init-and-update-submodules)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
