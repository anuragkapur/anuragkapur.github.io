---
layout: post
title:  "Datastax Cassandra Summit 2016"
date:   2016-04-19 12:00:00 +0000
categories: engineering highlight
tags: engineering
permalink: /blog/datastax-summit-2016
teaser: My notes from Datastax Cassandra Summit
img-url: /assets/blog/training/dse-summit/dse.png
---

## Making Connections With Graphs

* Relations DBs, joins, filtering, normal forms
* Relational db - schema changes as your use cases evolve become painful
    * Every entity gets a table
    * Lots of many to many tables
    * Rigid structure
    * Going from one to many requires a migration and new data model
* Solving problems with graph
    * Fundamentals
        * Vertex - a thing, example: Movie, Person
        * Edges - labeled, directional relationships

        JCVD -- acted in --> Time cop
             -- acted in --> Blood sport
             -- directed --> Blood sport

    * Properties - similar to fields in a table             
    * Power of graphs are relationships
    * Summary    
    ![Graph fundamentals summary](/img/content/datastax-summit-2016/datastax-summit-dse-summary.png)

    * Tinkerpop 3 & Gremlin - API for graph query

        g.V().has("person", "name", "JCVD")

* RDF stores vs Graph DBs
    * RDF - great for inferencing capabilities, but tend to not scale very well
    * RDF stores can be considered to be specialist graph DBs  
    * Good ref: https://www.quora.com/What-are-the-differences-between-a-Graph-database-and-a-Triple-store

* Ref: [datastax-enterprise-graph](http://www.datastax.com/products/datastax-enterprise-graph)            

## Data modelling

* Write path

        Data -> Memtable -> Commit log -> SSTable

* SSTable compaction
    * Compaction strategies
        * Size tiered
        * Leveled
        * Date tiered (sort of not recommended - use with care)
        * Time tiered (not available yet, may come)

* Data organisation
    * Partition key
    * Clustering key
    * Columns
    * Primary key = partition + clustering key

* Data modelling
    * Always include partition key in where clause of query
        * User login scenario - customer login by email

    ![Login scenario - Problem](/img/content/datastax-summit-2016/datastax-summit-dse-login-scenario.png)
    ![Login scenario - Solution](/img/content/datastax-summit-2016/datastax-summit-login-problem-solution.png)

    * User defined types and collections

    ![User defined types](/img/content/datastax-summit-2016/datatstax-summit-dse-user-defined-types.png)

    * Avoid client side joins from 2 or more tables
    * Customer registration problem
        * If an insert is done by 2 different clients at around the same time, the last write wins. This may be a
        problem in certain use-cases. Example: user registration by email
        * Solution ![User registration problem solution](/img/content/datastax-summit-2016/datastax-summit-dse-customer-registration-problem-solution.png)
        * IF NOT EXISTS - expensive, use with caution, when really required
    * Customer login problems
        * Customers, Customers_by_email
        * Materialized view w/ DSE 5.0   

## Scaling DataStax in Docker

* Key concepts
    * Images
    * Registries (example: Docker hub)
    * Containers - running instance of image
* DSE processes
    * Core DSE JVM
    * Opscentre agent
    * Spark executor processes
    * Single spark workder process
    * etc
* Things to consider
    * Host and DSE config
    * Cassandra data - where will you mount volumes etc
    * JVM heap size
    * Garbage colletor
* Default networking not recommended in prod, instead use host networking

        docker run -net=host

* Storage
    * commit log or anything else in /var/lib/data
* Ref: [https://github.com/joeljacobson/dse-docker](https://github.com/joeljacobson/dse-docker)    
