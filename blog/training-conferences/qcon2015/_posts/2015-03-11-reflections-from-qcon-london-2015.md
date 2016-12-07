---
layout: post
title:  "Reflections from QCon London 2015"
date:   2015-03-11 12:00:00 +0000   
categories: conferences highlight
permalink: /blog/reflections-from-qcon-london-2015
teaser: Reflections from QCon London
img-url: /assets/blog/training/reflections-from-qcon-longon-2015/qcon-2015.jpg
---

This year was my first time at QCon, one of the leading software engineering conferences across the world. I felt the 
talks were mixed bag - some good ones and some not so good ones.

My favourite talk at the conference was “Service Architectures at Scale” by Randy Shoup 
(https://www.linkedin.com/in/randyshoup). He started by talking about Architecture Evolution with examples from 
engineering organisations like Google, Twitter, Amazon, eBay etc. Architecture at most of these places started as giant
and hard to manage monolith or brittle hacks glued together. These then went through phases of refactoring to evolve 
into a solid set (in most cases, very large sets ~ 100s) of microservices, each bounded by a business context. Another 
important point made was that effective architecture comes from a decentralised, bottom-up approach. Centralised, 
top-down architecture, usually does not work. 

What seems like very careful and elegant layering of collaborating services is also something that evolves over the 
period and was designed bottom-up. An example of Google Service Layering is used to explain this idea. Each of the below
(from left to right) is built over the layer beneath:

_Cloud Store (NoSQL service) > Megastore (Geo-scaled - multi DC in a region structured DB) > Bigtable (DC level 
structured storage) > Colossus (Current generation of Google File System) > Borg (Google Cluster Management Platform)_

__Architecture evolves. Even the likes of Google, Twitter, Amazon don’t usually get it right the first time. So don’t try
to nail it and get it perfect in the first iteration.__

Randy then moves on to explore whether the whole idea of decentralised bottom up design is “architecture without an
Architect”? He says, it kind of is! He goes on to highlight that __there is no role or title at Google with the word 
“Architect” in it__ (and here I was going la-la about my recent promotion to the role of a Technical Architect!). An 
architecture style that is effective, even without a central governing body is one that asks the right questions and 
encourages teams to think about operational and other requirements they may forget otherwise. Simple way of achieving 
this could be a checklist saying - “did you think about x”, “what would happen when y goes down” etc etc. A good 
architect suggests and channels the teams into the right direction by getting teams to think about all important aspects
of both development and operational sustenance of services they own.

Architects like to come up with standards, I know I do. This is fine, but only as long as these __standards are 
encouraged, not enforced.__ You make the standard you want teams to use, so accessible and easy to work with that not 
taking it into consideration just becomes plain simple stupid. __You make doing the wrong thing hard and the right thing
easy__ and thereby achieve a good synergy of autonomy to the teams and an element of consistency and standardisation 
across these disparate teams. It is however imortant to note that standardisation of some areas is paramount to prevent
things from going out of control. At the end of the day multiple micro services, all part of the same ecosystem have to
communication with each other. So standardisation of things like network protocols, data formats, interface 
specification, source control system, monitoring, alerting, diagnosing etc makes sense and is important. But again, 
these should not be enforced. A good architect implements these standards by __making the standard better than the 
alternatives!__

Randy also mentions the ideas of __code-reviews and making all code searchable across the organisation__ as effective
ways of promoting standardisation. Imagine you are planning to use a system or library that you have never used before
and a search across all repos returns a list of examples of how it has been done before by other engineers and teams.
Pretty useful it would be, I say.

An idea that I really liked in the talk was to have different internal teams charge each other (yes, charging money) for
services they provide. I can see this as being an effective way to solve many problems I have seen in teams and 
technology departments I have worked in. A recent problem I have seen is that of alert fatigue. We are probably not 
quite there with regards to the dev-ops ethos (we are close though!). This means that separate “operations” and 
“support” teams are responsible for atleast out of hours support of services we build. This takes the pain of waking up
at 3am to fix a production issue away to some extent; actually it passes it from one team to another. But then it also
introduces other problems.

Since the development team isn’t looking at alerts from production systems all the time they tend to ignore the alert 
noise created by monitoring and alerting capabilities built into the service. The developers in the team want to improve
this, but at times this “improvement” work is trumped by higher priority “money-making” new feature development work. 
Now __imagine the out of hours support by the ops team were a service that dev teams paid for.__ Wouldn't it be an effective
way of prioritising the improvement work along with the new feature development? The support team could start charging
teams using a __"pay per alert we address"__ model. So now the Product Owner could either spend the money in new feature
development or save costs by allowing the team to address the alert noise.

The presence of a separate ops or support team poses another limitation in my view (and maybe this isn’t proper 
Devops?). The development team has limited choice with regards to the monitoring and alerting tools used, some platform
choices etc. You can’t have the dev teams use a diverse range of such tools and platforms else supporting them would be
hell for the ops team. Instead, if the dev team was responsible for 24 * 7 support of their service and platform, maybe
they could use whatever they want? The only requirement should be a Service Level Objective, i.e. the “What”, the tool
set and platform choice, i.e. the “How” should be left to the dev team? I think so! PS: I understand this can pose 
contractual issues in some organisations or dev team members may not be willing to be called out of hours without being
paid more. My point is, __this option should be available - choose whatever tooling / platform you want, but be prepared
to support your service 24*7. If you want to use the support team’s services, you have to abide by their tooling / 
platform preferences.__

The idea can be extended further to give autonomy and freedom to development teams. Imagine that your department has an
infrastructure and platforms team that builds tools and services for you to build your applications over. Or, the team 
of architects like you to use a specific set of tools and platforms. If you are happy with these tools and platform 
choices available, awesome, but developers are usually hard to please. Often they want to try out new (and shiny?) 
things. They may want to explore a PaaS option like Heroku, or try a containerisation approach using docker. Your 
infrastructure and platform team may not support this and restrict you to use a specific standard approach. I see this
as a problem. An effective solution could be, again, to start charging for all services. __If the development team has to
“pay” for any service (external or internal) it uses and the solution provided or recommended by your department’s 
infrastructure / architecture team is good and fit for purpose, it *will* be cheaper to use. If it isn’t dev team will
use something else__, maybe Heroku. __This way, the best option out there will bubble to the top, via the process of natural
selection.__ I think such an approach would do really well. At the end of the day, this is how encouraging a standard is 
different from mandating one. If as an architect, you want the dev teams to use a given set of tools and platforms, make
them super easy and cheap to use. If they aren’t, the dev teams won’t use them and you would know your choices weren't
the right ones.

Randy’s slide-deck can be found [here](http://www.slideshare.net/InfoQ/service-architectures-at-scale-lessons-from-google-and-ebay).