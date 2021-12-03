<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Moving around](#moving-around)
  - [Move to top of file](#move-to-top-of-file)
  - [Move to last line in file](#move-to-last-line-in-file)
  - [Move to last character in file](#move-to-last-character-in-file)
- [Operations](#operations)
  - [Replace spaces with new lines](#replace-spaces-with-new-lines)
  - [Delete all lines containing a pattern](#delete-all-lines-containing-a-pattern)
  - [Remove all lines](#remove-all-lines)
  - [Delete all chars from cursor to end of line](#delete-all-chars-from-cursor-to-end-of-line)
  - [Copy paste line](#copy-paste-line)
  - [Copy paste several lines](#copy-paste-several-lines)
  - [Move line](#move-line)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

---
layout: post
title:  "VIM cheat sheet"
teaser: Cheat sheet for the vim editor
date:   2016-03-08 22:11:26 +0000
categories: cheat-sheets
tags: cheat-sheets
---

# Moving around

## Move to top of file

    gg
    
## Move to last line in file

    G
    
## Move to last character in file

    G$

# Operations

## Replace spaces with new lines

    :%s/ /^M/g    

The `^M` is typed using Ctrl-V-Enter

## Delete all lines containing a pattern

    :g/pattern/d

## Remove all lines

    :0
    dG
    
## Delete all chars from cursor to end of line

    d$
    
## Copy paste line
```shell
Y ("yank")
p ("put below")
P ("put above")
```

## Copy paste several lines
```shell
11yy ("yank 11 lines")
p ("put below")
P ("put above")
```

## Move line
```shell
dd ("delete")
p ("put below")
P ("put above")
```
    
