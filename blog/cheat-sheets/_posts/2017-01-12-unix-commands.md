---
layout: post
title:  "Unix commands cheat sheet"
teaser: Cheat sheet for misc unix commands
date:   2017-01-12 10:37:00 +0000
categories: cheat-sheets
---

# System administration
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

# Utilities

## SSH tunnel - forward traffic from a specific localhost port to a specific remote host and port
```shell
ssh -L <localhost_port>:<remote_host>:<remote_port> <username>@<tunnel_server>
```

## SSH tunnel - forward traffic from a specific localhost port to remote host
```shell
ssh -D <localhost_port> -C -q -N <username>@<tunnel_server>
```

## Download file using curl
```shell
$ curl -O <url>
```

## Upload file using curl
```shell
$ curl --verbose -F 'file=@"/tmp/myFile.txt"' http://localhost:3000/api/myFileEndpoint
```

## Simple load testing shell script
Measures time in seconds
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

# CentOS
## Manage network interfaces
```shell
$ nmtui
```

# Ubuntu
```shell
mkdir $HOME/Shared
/usr/bin/vmhgfs-fuse -o auto_unmount .host:/ $HOME/Shared
```


