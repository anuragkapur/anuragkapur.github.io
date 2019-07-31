---
layout: post
title:  "Webstorm node.js debugger error when using ES6 and babel"
date:   2019-06-30 00:00:00 +0000   
categories: node babel issue-resolution
teaser: Solution to Unexpected Identifier error when debugging a ES6 node.js app in Webstorm
---  

## Issue
```
Debugger listening on ws://127.0.0.1:61115/dd5797d2-948b-4fe4-8ce0-2fad10a118ca
For help, see: https://nodejs.org/en/docs/inspector
Debugger attached.
Launching quizalize in DEV MODE
/Users/anuragkapur/tech-stuff/workspace/zzish/quizalize/src/server/quizalize.js:3
import express from "express";
       ^^^^^^^

SyntaxError: Unexpected identifier
```

## Resolution
![Webstorm debug configuration](assets/blog/issue-resolutions/nodejs-debugger-error-babel-fix.png)

## Ref
* [https://intellij-support.jetbrains.com/hc/en-us/community/posts/203373470-How-to-make-Webstorm-2016-2-debug-work-with-ES6-and-babel](https://intellij-support.jetbrains.com/hc/en-us/community/posts/203373470-How-to-make-Webstorm-2016-2-debug-work-with-ES6-and-babel)
* [https://intellij-support.jetbrains.com/hc/en-us/community/posts/115000380044--node-debug-and-node-debug-brk-are-invalid-Please-use-node-inspect-or-node-inspect-brk-instead](https://intellij-support.jetbrains.com/hc/en-us/community/posts/115000380044--node-debug-and-node-debug-brk-are-invalid-Please-use-node-inspect-or-node-inspect-brk-instead)



