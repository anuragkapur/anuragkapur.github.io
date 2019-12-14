---
layout: post
title:  "Jenkins maven job failure"
date:   2016-03-10 16:37:00 +0000   
categories: jenkins ci issue-resolution
tags: issue-resolutions
teaser: Debugging mysterious maven job failure in jenkins
---  

## Problem Statement

Jenkins job with a configured maven build step fails without any info on cause

Console output as follows

    16:27:23  > /usr/bin/git config core.sparsecheckout # timeout=10
    16:27:23  > /usr/bin/git checkout -f d5e46fca334506664aba5a0f87baad7232b22944
    16:27:23  > /usr/bin/git rev-list d5e46fca334506664aba5a0f87baad7232b22944 # timeout=10
    16:27:23 [workspace] $ mvn -s /home/jenkins/.m2/settings.xml -Dmaven.repo.local=/var/lib/jenkins/jobs/crypto-signatures/workspace/.repository versions:set -DnewVersion=0.27.0
    16:27:23 Build step 'Invoke top-level Maven targets' marked build as failure
    16:27:23 [workspace] $ mvn -s /home/jenkins/.m2/settings.xml -Dtag=0.27.0 -DconnectionUrl=scm:git:git@github.com:Financial-Times/crypto-signatures.git -Dmaven.repo.local=/var/lib/jenkins/jobs/crypto-signatures/workspace/.repository scm:tag
    16:27:23 Build step 'Invoke top-level Maven targets' marked build as failure
    
## Resolution

Explicitly select maven version in job configuration
    
![jenkins config](/img/content/jenkins-job-maven.png)    
