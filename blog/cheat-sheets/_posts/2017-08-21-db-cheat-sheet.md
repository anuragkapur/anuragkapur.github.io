---
layout: post
title:  "Database commands cheat sheet"
teaser: Cheat sheet for various DB commands
date:   2017-08-21 17:04:00 +0000
categories: cheat-sheets
---

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