---
layout: post
title:  "MacOS cheats"
teaser: Cheat sheet for MacOS
date:   2016-09-27 22:11:26 +0000
categories: cheat-sheets
tags: cheat-sheets
---

## Brew

### List installed brew packages
```shell
brew list
```

### Uninstall a package installed via brew
```shell
brew uninstall <package_name>
```
### List services
```bash
$ brew services list
Name  Status  User        Plist
redis started anuragkapur /Users/anuragkapur/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

## Disable apple security that prevents packages by unidentified developers from being opened (tested on macOS Sierra)

```shell
$ sudo spctl --master-disable
$ sudo spctl --master-enable
```

## Utilities

### Find process using a specific port
```bash
$ sudo lsof -i tcp:8080
```

