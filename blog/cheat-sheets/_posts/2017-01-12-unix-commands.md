---
layout: post
title:  "Unix commands cheat sheet"
teaser: Cheat sheet for misc unix commands
date:   2017-01-12 10:37:00 +0000
lastUpdatedDate: 2021-06-29 00:00:00 +0000
categories: cheat-sheets
tags: cheat-sheets
---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [System administration](#system-administration)
  - [Find PID using a given port number](#find-pid-using-a-given-port-number)
  - [Find disk usage per directory](#find-disk-usage-per-directory)
  - [Delete all files more than x days old](#delete-all-files-more-than-x-days-old)
  - [Delete everything except files with given extension](#delete-everything-except-files-with-given-extension)
  - [Measure response time with curl](#measure-response-time-with-curl)
- [Utilities](#utilities)
  - [SSL Keys](#ssl-keys)
    - [Convert .p12 to .key](#convert-p12-to-key)
    - [Convert .crt to .pem](#convert-crt-to-pem)
  - [SSH tunnel - forward traffic from a specific localhost port to a specific remote host and port](#ssh-tunnel---forward-traffic-from-a-specific-localhost-port-to-a-specific-remote-host-and-port)
  - [SSH tunnel - forward traffic from a specific localhost port to remote host - can also be used to setup SOCS proxy](#ssh-tunnel---forward-traffic-from-a-specific-localhost-port-to-remote-host---can-also-be-used-to-setup-socs-proxy)
  - [Download file using curl](#download-file-using-curl)
  - [Upload file using curl](#upload-file-using-curl)
  - [Rename all files in a directory with sequential numbers](#rename-all-files-in-a-directory-with-sequential-numbers)
  - [Simple load testing shell script](#simple-load-testing-shell-script)
  - [Sort file in a directory by name and print size and file name](#sort-file-in-a-directory-by-name-and-print-size-and-file-name)
- [CentOS](#centos)
  - [Manage network interfaces](#manage-network-interfaces)
- [Ubuntu](#ubuntu)
- [AWS CLI](#aws-cli)
  - [S3 copy/download](#s3-copydownload)
  - [S3 upload object](#s3-upload-object)
  - [EB get saved config](#eb-get-saved-config)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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

## SSL Keys

### Convert .p12 to .key
```shell
openssl pkcs12 -in private_key.p12 -nodes -out private.key -nocerts
```

### Convert .crt to .pem
```shell
openssl x509 -in STAR_quizalize_com.crt -out STAR_quizalize_com.pem -outform PEM
```

## SSH tunnel - forward traffic from a specific localhost port to a specific remote host and port
```shell
ssh -L <localhost_port>:<remote_host>:<remote_port> <username>@<tunnel_server>
```

## SSH tunnel - forward traffic from a specific localhost port to remote host - can also be used to setup SOCS proxy
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

## Rename all files in a directory with sequential numbers
```bash
a=1
for i in *.jpg; do
  new=$(printf "erg-%02d.jpg" "$a") #04 pad to length of 4
  mv -i -- "$i" "$new"
  let a=a+1
done
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

## Sort file in a directory by name and print size and file name
```shell
ls -ltr | sort -k 9 | awk '{print $5":"$9}'
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

## Switch between apt-get installed java versions
```
sudo update-alternatives --config java
```

# AWS CLI
## S3 copy/download
```shell
aws s3 cp s3://<bucket-name>/<path-to-file> /tmp/. --region=eu-central-1
```

## S3 upload object
```shell
aws s3 cp /Users/anuragkapur/Desktop/hello-world.txt s3://<bucket-name>/ --profile <cli-credentials-profile-name>
```

## EB get saved config
```shell
eb config get NAME
```

## Cloud Watch - Describe Subscription Filters
```shell
aws logs describe-subscription-filters --log-group-name myLogGroup --region ap-southeast-1
```

## Cloud Watch - Update Subscription Filter
```shell
aws logs put-subscription-filter --log-group-name myLogGroup --filter-name myFilterName --filter-pattern "{($.userId = *) || ($.data[0].userId = * )}" --destination-arn destinationArn --region eu-central-1 
```