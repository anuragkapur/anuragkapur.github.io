---
layout: post
title:  "Database commands cheat sheet"
teaser: Cheat sheet for various DB commands
date:   2017-08-21 17:04:00 +0000
categories: cheat-sheets
tags: cheat-sheets
---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [PostgreSQL](#postgresql)
  - [Connect via psql](#connect-via-psql)
  - [Create User and DB](#create-user-and-db)
  - [Drop DB](#drop-db)
  - [Show schemas - psql cli](#show-schemas---psql-cli)
  - [Show tables - psql cli](#show-tables---psql-cli)
  - [Show tables in a schema](#show-tables-in-a-schema)
  - [Quit postgres prompt](#quit-postgres-prompt)
  - [Generate dump](#generate-dump)
  - [Import .dump](#import-dump)
- [Redis](#redis)
  - [Flush all keys](#flush-all-keys)
- [MongoDB](#mongodb)
  - [Connect to a DB](#connect-to-a-db)
  - [Switch/Use DB](#switchuse-db)
  - [Show collections in DB](#show-collections-in-db)
  - [Copy docs from remote db collection into current db](#copy-docs-from-remote-db-collection-into-current-db)
  - [Copy database](#copy-database)
  - [Delete docs from collection that don't match criteria](#delete-docs-from-collection-that-dont-match-criteria)
  - [Export collection](#export-collection)
  - [Find docs that have a certain attribute defined](#find-docs-that-have-a-certain-attribute-defined)
  - [Sort in reverse natural order (most recently created first)](#sort-in-reverse-natural-order-most-recently-created-first)
- [Neo4j](#neo4j)
  - [Delete all nodes](#delete-all-nodes)
  - [List all nodes](#list-all-nodes)
  - [Count nodes](#count-nodes)
  - [Find nodes with a property value](#find-nodes-with-a-property-value)
  - [Find nodes with a specific attribute and relationship attribute](#find-nodes-with-a-specific-attribute-and-relationship-attribute)
  - [Find nodes with a specific attribute and a path (of may length 3) to a node with certain attribute](#find-nodes-with-a-specific-attribute-and-a-path-of-may-length-3-to-a-node-with-certain-attribute)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# PostgreSQL

## Connect via psql
```bash
$ psql -h <hostname> -p <port> -U <user> <db_name>
```

## Create User and DB
```bash
$ psql -U <username>
DROP DATABASE <dbname>;
CREATE USER <username> WITH PASSWORD '<password>';
CREATE DATABASE <dbname> OWNER <username>;
CREATE DATABASE optimization OWNER tactical;
```

## Drop DB
```bash
$ dropdb -U <username> <dbname>
```

## Show schemas - psql cli
```bash
\dn
```

## Show tables - psql cli
```bash
\dt
```

## Show tables in a schema
```bash
\dt <schema_name>.
```

## Quit postgres prompt
```bash
postgres-> \q
```

## Generate dump
```bash
pg_dump -h <server_hostname> -U <username>  -f db.dump <db_name>
```

## Import .dump
```bash
psql -h <server_hostname> -U <user> <db_name> < <PATH TO DUMP>
```

# Redis

## Flush all keys
```bash
$ redis-cli -c -h $redis_endpoint -p $port flushall
```

# MongoDB

Ref: [Mongo Shell reference](https://docs.mongodb.com/manual/reference/mongo-shell/)

## Connect to a DB
```bash
$ mongo --host localhost -u <username> --authenticationDatabase <dbname> -p <paassword>
```

## Switch/Use DB
```bash
> use admin;
switched to db admin
```

## Show collections in DB
```bash
> show collections;
mycollection
system.users
system.version
```

## Copy docs from remote db collection into current db
```javascript
db.getSiblingDB("remotedb").runCommand(
    { 
        cloneCollection: "remotedb.curriculumNodes",
        from: "remote.host:27017",
        query: {  }
    }
)
```

## Copy database
```javascript
db.copyDatabase("original-db-name", "original-db-name-backup")
```

## Delete docs from collection that don't match criteria
```javascript
db.getCollection('usergroup').deleteMany({uuid: {$nin: ['b068c3ac-6a1d-4500-9121-18a6ef980b71']}})
```

## Export collection
```
mongoexport --db test --collection traffic --out traffic.json
```

## Find docs that have a certain attribute defined
```javascript
db.getCollection('user').find({google: {$exists: true}})
```

## Sort in reverse natural order (most recently created first)
```javascript
db.getCollection('session').find({}).sort({$natural: -1})
```

# Neo4j
## Delete all nodes
```
match (n) detach delete n
```

## List all nodes
```
match (n) return n
```

## Count nodes
```
match (n:Person) return count(n) as count
```

## Find nodes with a property value
```
match (n:Student) where n.name = 'Anurag' return n
```

## Find nodes with a specific attribute and relationship attribute
```
match (subject)-[:IS_SUBJECT_OF*]->(curriculum) 
where 
curriculum.name='Philippines Curriculum' and 
subject.importKey='29/05/19 philippines curriculum' 
return subject
```

## Find nodes with a specific attribute and a path (of may length 3) to a node with certain attribute
```
match (n)-[*0..3]->(curriculum:Curriculum) 
where 
curriculum.name='Philippines Curriculum' and 
n.importKey='29/05/19 philippines curriculum' 
detach delete n
```
OR
```
match(n { importKey:"29/05/19 philippines curriculum"}) - [* 0..3] -> (curriculum: Curriculum {uuid:"lol"})
detach delete n
```