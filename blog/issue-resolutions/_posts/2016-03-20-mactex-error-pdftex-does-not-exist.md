---
layout: post
title:  "Mactex error - pdftex does not exist"
date:   2016-03-20 13:04:00 +0000
categories: tex maxtex texshop issue-resolution
tags: issue-resolutions
teaser: Debugging mactex error while generating pdf file using texshop
---

## Problem Statement

Opening a valid .tex file using TeXShop to generate a pdf file resulted in the
following error and suggested that the mactex installation was either missing
or corrupt

    /usr/texbin/pdflatex does not exist

## Resolution

Instead of re-installing, the problem was fixed by changing the default
configured pdftex engine path setting in TeXShop. (TeXShop > Preferences >
Engine > Path)

Obtain correct bath by running the following command on the terminal

    $ which pdftex
    /Library/TeX/texbin/pdftex
