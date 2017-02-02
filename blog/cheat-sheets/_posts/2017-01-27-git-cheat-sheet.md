---
layout: post
title:  "GIT cheat sheet"
teaser: Cheat sheet for the GIT command line
date:   2017-01-27 12:09:26 +0000
categories: cheat-sheets
---

# Commits, reverts etc

## Revert commited changes to a single file
```shell
$ git checkout <revision number to revert to> <file path>
$ git commit
```

# Branches

## Delete remote branch
```shell
$ git push origin --delete <branch-name>
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
