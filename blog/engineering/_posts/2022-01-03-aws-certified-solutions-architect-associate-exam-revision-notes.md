---
layout: post
title:  "AWS Certified Solutions Architect - Associate - Exam Revision Guide"
date:   2022-01-03 00:00:00 +0000   
categories: engineering
tags: engineering
teaser: Notes taken while taking the A Cloud Guru course to prepare for the certification exam
---

### Simple Queue Service (SQS)
* Max message size is 256 KB of text in any format
* Default message retention period is 4 days, min is 1 minute and max is 14 days
* Delivery delay: default is 9 and can be set to a max of 15 minutes
* Queue types: standard and FIFO
* Use FIFO is message ordering is important
* Polling types: long and short polling
* Max long polling wait time is 20 seconds
* Long polling helps reduce cost of using SQS by elimination the number of empty responses and false empty responses
* SQS can duplicate messages but this only happens once in a while; if happening consistently check for misconfigured
visibility timeout, or missing consumer logic to delete the message after successful processing
* Messages are encrypted in transit by default and encryption at rest can be optionally added
* Dead letter queue (DLQ) is a standard SQS queue to send messages that failed being processed to for review
* Max receives setting in DLQ defines how many times the message may be retried in the main queue before being sent to 
DLQ
* CloudWatch can be used to monitor queue depth of DLQ

### Simple Notification Service (SNS)
* Used for proactive push notifications
* Can be used to set up alarms in CloudWatch
* Available subscribers: Kinesis data firehose, SQS, Lambda, email, HTTP(S), SMS, platform application endpoint
* Retry is only available with HTTP(S) subscribers
* Max message size is 256 KB of text (same as SQS)
* Has DLQ support
* FIFO and Standard SNS topics available
* Messages are encrypted in transit by default and encryption at rest can be optionally added

### API Gateway
* Notable features
  * Web Application Firewall (WAF)
  * Rate limiting and DDoS protection