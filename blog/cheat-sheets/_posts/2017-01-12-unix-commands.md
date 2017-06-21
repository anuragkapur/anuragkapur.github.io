---
layout: post
title:  "Unix commands cheat sheet"
teaser: Cheat sheet for misc unix commands
date:   2017-01-12 10:37:00 +0000
categories: cheat-sheets
---

## Find PID using a given port number
```shell
lsof -i :6234
```

## Find disk usage per directory
```shell
find . -maxdepth 1 -type d -exec du -sh {} \;
```
or       
```shell
find . -maxdepth 1 -type d | xargs du -sh
```

## Delete all files more than x days old
```shell
find /path/to/directory/ -mindepth 1 -mtime +5 -delete
```

## Delete everything except files with given extension
```shell
$ find . ! -name "*.jar" | xargs rm -rf
```

## Measure response time with curl
```shell
$ curl -o /dev/null -s -w %{time_total} http://www.example.com/
```

## Simple load testing shell script
```shell
#!/bin/bash

echo "fastlyTime,awsGatewayTime"

while true
do
  fastlyTime=`curl -o /dev/null -s -w %{time_total} -H 'X-Api-Key: bla' https://round-trippa.ft.com/callback`
  sleep 1
  awsGatewayTime=`curl -o /dev/null -s -w %{time_total} -H 'X-Api-Key: bla' https://round-trippa-gw-eu-west-1-prod.memb.ft.com/callback`
  sleep 1
  echo "${fastlyTime},${awsGatewayTime}" >> responsetimes.log
done
```
