---
layout: post
title:  "Facebook Modile Devcon - London 2013"
date:   2013-05-02 12:00:00 +0000   
categories: highlight engineering
tags: engineering
teaser: Facebook Mobile DevCon was a great day out with plenty of informative sessions, including ones that dived into code.
img-url: /assets/blog/engineering/fb-mobile-devcon-2013/fb-mobile-devcon.jpg
---

Facebook Mobile DevCon was a great day out with plenty of informative sessions, including ones that dived into code.

Here are some notes from a few talks / sessions I attended.

## How Facebook Builds Facebook for iOS
Facebook started with a web approach, which was a native app with essentially a Web View that did everything

### Web Approach - HTML as an App Platform    
Pros
* Instant updates
* A/B testing
* Multi platform software development - one code base (more or less)

Cons
* Frequent performance problems
* No coherent multithreading strategy
* Difficult memory management
* Debugging and getting stack traces was difficult

### Native App Approach
* Advanced features like Core Animation, Core Data were used. These features require a lot of time spent on them but work great when you master them
* Internally dog-fooded for 3 months
* Great performance which everyone loved

### Team Structure
* Core team - building shared libraries, infrastructure
* Product team - makes the product, on top of the shared libraries and infrastructure created by core team
* Release team

### Lessons Learnt / Tips
* Fixed release cycle - Ship every x weeks no matter what instead of having feature releases - when working with several interdependent teams
* Build features with an off switch

### Development Process
* Emphasis on developer velocity - from concept to shipped
* You cannot break master
* Make changes locally
* Post changes for review BEFORE committing to master
* Changes go to an open sourced tool called __Phabricator__ for review instead of master
* Automated review of code in addition to manual
* arc lint
* checkstyles - indentation etc
* compiler warnings, deprecation messages, common errors - rules can be created

They use images like these in Phabricator as code review feedback, which I think is awesome ;)  

![Pharbicator Review Images](/assets/blog/engineering/fb-mobile-devcon-2013/fb-phabricator-pr-images.jpg)

### Buildbot - CI tool
* Dogfood internally
* uses iOS enterprise certificates
* use different bundle ids and icons for different types of builds

### Branching
* master - experiments, feature development and stabilisation happens here
* release - a tool called releeph is used. Automated merge. More analytics on size of change, churn (review comments), developer karma available here.

### Testing
* No “Test Engineers” or “QA” departments
* TDD
* Unit testing - OCMock and SenTestingKit
* Unit testing on iOS is not ideal
* no dependency injection
* UIAutomation can use some improvement
* xcodebuild not ideal - doesn’t run simulator tests
* xctool - open sourced by Facebook. Runs simulator tests and gives structured output amoung other improvements
* Internal settings - great idea to include in any native app - to turn features on/off at runtime Iterate quickly

## The Facebook SDK for iOS
### FB SDK Layers
* Core
* Graph
* Native UI

### Using the SDK
* FacebookDisplayName is new plist entry in v3.5 and weird things happen if you don’t have this. Debugging can be hard. So make sure this is there
* Login - OS integrated
* FB share - default text cannot be added automatically. User has to add it. Most common policy violation

### Sharing is important
* Options
  - Native iOS 6 share sheet. Only works when someone has FB configured as an account on their iOS device.
  - Native share dialog using FB app already installed. Uses Fast app switch.
  - Native share with openGraph - you can use your own interface with this option
  
### Deep linking - Drives growth of your app
* Take a user direct into your app and onto the story they shared from the Facebook app

### Facebook Login - Best Practices
* Don’t randomly ask for permissions. Instead ask when the user is in the mindset to give you permissions. For example, when a user first decides to post, ask for write permissions.    
![FB Permission Issues](/assets/blog/engineering/fb-mobile-devcon-2013/fb-permissions.jpg)  
  

