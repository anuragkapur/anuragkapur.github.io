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
CREATE USER <username> WITH PASSWORD '<password>';
CREATE DATABASE <dbname> OWNER <username>;
CREATE DATABASE optimization OWNER tactical;
```

## Show tables - psql cli
```bash
\dt
```

## Import .dump
```bash
psql -U <user> <db_name> < <PATH TO DUMP>
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
