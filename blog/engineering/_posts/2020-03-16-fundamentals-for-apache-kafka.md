---
layout: post
title:  "Fundamentals for Apache Kafka"
date:   2020-03-16 11:00:00 +0000   
categories: engineering
tags: engineering
teaser: Resources and notes from Kafka fundamentals webinar
---

<iframe src="/assets/blog/engineering/apache-kafka/slidesapachekafkaarchitecturefundamentalsexplained1579807020653.pdf" width="100%" height="400"></iframe>
Slides: [Webinar slides](/assets/blog/engineering/apache-kafka/slidesapachekafkaarchitecturefundamentalsexplained1579807020653.pdf)

* Brokers rely on local storage instead of network storage like SAN, NAS for low i/o latency
* Zookeeper is used to store metadata for cluster management, secrets etc
* Producer-topic and consumer-topic both have a many-to-many relationship
* How much control do I as a user have on the partition replica location. Example: can I configure replicas of a 
partition to be stored on brokers that belong to a different Availability Zone in AWS?
  * Yes you can. The basic recommendation for that is the usage of the broker property 
  "broker.rack" = (cf. http://kafka.apache.org/documentation.html#basic_ops_racks )
* No. of partitions of a topic - is this something kafka decides internally, or is this something a user configures? 
Can this number change during the life of a topic for horizontal scaling - i.e when the message volume needs to be 
scaled up?
  * The number of partitions of a topic is one of the most important settings of Kafka, and it's normally configured by 
  users. Because it affects other parts of the architecture (key distribution, number of clients in a client group, 
  number of "replicas" in Kafka Stream application) we don't recommend to change this setting during the lifetime of a 
  topic. It can be however oversubscribed without much impact (e.g. you can start with 10-20 partition even if you have 
  a 3-node cluster).

