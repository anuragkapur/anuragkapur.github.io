---
layout: post
title:  "MacOS cheats"
teaser: Cheat sheet for MacOS
date:   2016-09-27 22:11:26 +0000
categories: cheat-sheets
---

## Disable apple security that prevents packages by unidentified developers from being opened (tested on macOS Sierra)

```shell
$ sudo spctl --master-disable
$ sudo spctl --master-enable
```
