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
