---
layout: post
title:  "VIM cheat sheet"
teaser: Cheat sheet for the vim editor
date:   2016-03-08 22:11:26 +0000
categories: cheat-sheets
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

## Remove all lines

    :0
    dG
    
## Delete all chars from cursor to end of line

    d$
