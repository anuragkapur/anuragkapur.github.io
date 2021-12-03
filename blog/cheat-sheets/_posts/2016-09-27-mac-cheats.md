<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Brew](#brew)
  - [List installed brew packages](#list-installed-brew-packages)
  - [Uninstall a package installed via brew](#uninstall-a-package-installed-via-brew)
  - [List services](#list-services)
- [Disable apple security that prevents packages by unidentified developers from being opened (tested on macOS Sierra)](#disable-apple-security-that-prevents-packages-by-unidentified-developers-from-being-opened-tested-on-macos-sierra)
- [Utilities](#utilities)
  - [Find process using a specific port](#find-process-using-a-specific-port)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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

