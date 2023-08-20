---
layout: post
title:  "AWS Certified Solutions Architect - Associate - Exam Revision Guide"
date:   2022-01-03 00:00:00 +0000   
lastUpdatedDate: 2023-03-11 00:00:00 +0000
categories: engineering
tags: engineering aws certification
teaser: Notes taken while taking the ACloudGuru and AWS Skill Builder courses to prepare for the certification exam
---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [Exam Domains and Overview (SAA-CO3)](#exam-domains-and-overview-saa-co3)
  - [Recommended Whitepapers](#recommended-whitepapers)
- [AWS Fundamentals](#aws-fundamentals)
- [Simple Storage Service (S3)](#simple-storage-service-s3)
- [Elastic Compute Cloud (EC2)](#elastic-compute-cloud-ec2)
- [Simple Queue Service (SQS)](#simple-queue-service-sqs)
- [Simple Notification Service (SNS)](#simple-notification-service-sns)
- [API Gateway](#api-gateway)
- [Redshift](#redshift)
- [Elastic Map Reduce (EMR)](#elastic-map-reduce-emr)
- [Kinesis](#kinesis)
- [Athena and Glue](#athena-and-glue)
- [AWS Lambda](#aws-lambda)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Exam Overview (SAA-CO3)
### Exam domains
1. Design secure architectures - 30%
2. Design resilient architectures - 26%
3. Design high-performing architectures - 24%
4. Design cost-optimised architectures - 20%

### Key services to know for the exam
* Compute: EC2, Lambda, Elastic Beanstalk
* Storage: S3, EBS, EFS, FSx, Storage Gateway
* Databases: RDS, DynamoDB, Redshift
* Networking: VPCs, Direct Connect, Route 53, API Gateway, AWS Global Accelerator

### Misc
* 65 questions (50 scored and 15 un-scored); 130 minutes

### Recommended Whitepapers
* [AWS Well-Architected Framework](/assets/blog/engineering/wellarchitected-framework.pdf)
* [AWS Security Best Practices](https://docs.aws.amazon.com/whitepapers/latest/introduction-aws-security/security-of-the-aws-infrastructure.html)

## AWS Fundamentals
* AWS global infrastructure
  * 24+ regions, 77+ availability zones, 215+ edge locations
  * Edge locations are networking points of presence typically used for caching content (using CloudFront)
* 6 pillars of well-architected framework
  * Operational Excellence
  * Performance Efficiency
  * Security
  * Cost Optimisation
  * Reliability
  * Sustainability

## Identity and Access Management (IAM)
* IAM does not require region selection; it's a global service
* Policy documents
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "*",
      "Resource": "*"
    }
  ]
}
```
* Policy documents can be attached to groups, users (not recommended; users should inherit policy from groups instead) and roles
* AWS Security Token Service (AWS STS) can be used to, among other things, allow IAM users to assume a role with specific permissions as set out in an IAM policy

## Simple Storage Service (S3)
* Object-based storage for files up to 5 TB
* No limit on total volume of date and number of objects that may be stored
* S3 has a universal namespace (https://bucket-name.s3.region.amazonaws.com/key-name)
* Buckets are private by default
* You have to allow public access on both the bucket and its objects in order to make the bucket public
* Use object ACLs to make individual objects public
* Use bucket policies to make entire buckets public
* S3 storage classes

| Storage Class                 | Availability and Durability            | AZs | Comments                                            |
|-------------------------------|----------------------------------------|-----|-----------------------------------------------------|
| S3 Standard                   | 99.99% availability; 11 9's durability | >=3 |
| S3 Standard-infrequent access | 99.9% availability' 11 9's durability  | >=3 |
| S3 One zone-infrequent access | 99.5% availability; 11 9's durability  | 1   |
| S3 Glacier                    | 99.99% availability; 11 9's durability | >=3 | Access/retrieval time can be a few hours or minutes |
| S3 Glacier Deep Archive       | 99.99% availability; 11 9's durability | >=3 | Default retrieval time of 12 hours                  |
| S3 Intelligent-tiering        | 99.9% availability; 11 9's durability  | >=3 | For unknown or unpredictable access patterns        |

* Use S3 object lock to store objects using write once, read many (WORM) model
* Object locks can be on individual objects or applied to the bucket as a whole
* Object locks can be applied in governance or compliance mode
  * Governance mode: users can't overwrite or delete an object version or alter its lock settings unless they have special permissions
  * Compliance mode: no one, including root user of AWS account to overwrite or delete a protected object version
* Glacier uses vault lock which are equivalent to object locks in S3
* Encryption in transit: SSL/TLS
* Encryption at rest: Server-side encryption, SSE-S3, SSE-KMS, SSE-C (customer managed)
* Client-side encryption: you encrypt before sending to S3
* Encryption can be enforced with bucket policies
* Bucket-name/folder1/subfolder1/file.ext: folder1/subfolder1 is the prefix
* 3,500 PUT/COPY/POST/DELETE and 5,500 GET/HEAD request per second, per prefix are supported
* For better performance, spread your reads across different prefixes
* When using SSE-KMS, beware of KMS account level quotas
* Use multipart upload to increase performance when uploading files
* Should be used for any file over 100 MB and myst be used for any files over 5 GB
* Use S3 byte-range fetches to increase performance when downloading files from S3
* Objects can be replicated across bucket (in same of different regions) using S3 replication
* When S3 replication is turned on, existing objects in a bucket are not replicated automatically
* With S3 replication delete markets are not replicated by default

## Elastic Compute Cloud (EC2)
* Pricing options
  * On-demand
  * Spot (discount up to 90%)
  * Reserved
  * Dedicated (not multi-tenant hardware)
* Prefer IAM roles over use of access/secret keys
* Policies are attached to IAM roles and the changes to attached policies take immediate effect
* IAM roles can be attached/detached to running EC2 instances without having to stop/terminate
* Security groups: all inbound traffic is restricted and all outbound traffic is allowed, by default
* User data (bootstrap scripts) can access metadata (such as instance name, public IP etc)
* 

## Simple Queue Service (SQS)
* Max message size is 256 KB of text in any format
* Default message retention period is 4 days, min is 1 minute and max is 14 days
* Delivery delay: default is 9 and can be set to a max of 15 minutes
* Queue types: standard and FIFO
* Use FIFO if message ordering is important
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

## Simple Notification Service (SNS)
* Used for proactive push notifications
* Can be used to set up alarms in CloudWatch
* Available subscribers: Kinesis data firehose, SQS, Lambda, email, HTTP(S), SMS, platform application endpoint
* Retry is only available with HTTP(S) subscribers
* Max message size is 256 KB of text (same as SQS)
* Has DLQ support
* FIFO and Standard SNS topics available
* Messages are encrypted in transit by default and encryption at rest can be optionally added

## API Gateway
* Notable features
  * Web Application Firewall (WAF)
  * Rate limiting and DDoS protection

## Redshift
* Can store up to 16 PB of data
* A relational database
* A redshift cluster lives in a single AZ and thus not highly available

## Elastic Map Reduce (EMR)
* EMR cluster nodes are EC2 instances and thus live inside a VPC
* EC2 spot and reserved instances can be used to reduce EMR cluster costs

## Kinesis
* Real-time data streaming service
* 2 types of Kinesis services
  * Data streams: real-time streaming for ingesting data; does not scale automatically
  * Data firehouse: (near real-time) data transfer tool to get information to S3, Redshift, Elasticsearch, or Splunk; 
  scaling is managed by AWS
* Kinesis can store data for uo to a year as opposed to SQS which has a max 14 day retention period
* Kinesis Data Analytics allows data transformation using SQL as it flows through Kinesis

## Athena and Glue
* Athena is a serverless interactive query service that can analyse data in S3 using SQL
* Glue is serverless data integration service for ETL workloads
* Glue can be used to build a schema of data and Athena can use used to query this data stored in S3

## AWS Lambda
* 15 min max timeout
* 10 GB max RAM/memory
* Can run in or out of a VPC
