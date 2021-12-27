---
layout: post
title:  "Rust Reference Guide"
date:   2020-12-18 00:00:00 +0000   
lastUpdatedDate: 2020-12-18 00:00:00 +0000
categories: programming rust
tags: programming
teaser: My Rust reference guide, created when taking courses, experimenting and coming across stuff during projects 
img-url: /assets/blog/programming/rust_programming_language_black_logo.svg.png
permalink: /blog/rust-reference-guide
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Rustup - CLI](#rustup---cli)
  - [Check versions](#check-versions)
  - [Update version](#update-version)
  - [Launch docs](#launch-docs)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Rustup - CLI
### Check versions
```
% rustup --version
```
### Update version
```
% rustup update
```
### Launch docs
```
% rustup doc
```

## Cargo - CLI
### Create new project
```
% cargo new <project_name>
```
### Build/Compile
```
% cargo build

# build for release
% cargo build --release
```
### Update dependency versions in Cargo.lock
```
% cargo update
```
### Build and Run
```
% cargo run
```
### Compile but don't generate executable/binary
```
% cargo check
```
### Open docs for project (including dependencies)
```
cargo doc --open
```
