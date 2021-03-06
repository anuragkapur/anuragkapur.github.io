---
layout: post
title:  "Containers cheat sheet"
teaser: Containers cheat sheet - docker, kubernetes, eks
date:   2020-07-29 00:00:00 +0000
categories: cheat-sheets
tags: cheat-sheets
permalink: /blog/cheat-sheets/containers
---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Docker](#docker)
  - [View images](#view-images)
  - [Build image from dockerfile](#build-image-from-dockerfile)
  - [Remove image](#remove-image)
  - [Run an image](#run-an-image)
  - [Stop a container](#stop-a-container)
  - [List containers](#list-containers)
  - [Docker system cleanup](#docker-system-cleanup)
  - [Login and pull image from AWS ECR](#login-and-pull-image-from-aws-ecr)
  - [Push image to container registry](#push-image-to-container-registry)
  - [Copy file from container to localhost](#copy-file-from-container-to-localhost)
  - [SSH into container](#ssh-into-container)
- [Kubernetes](#kubernetes)
  - [Get pods and node info](#get-pods-and-node-info)
    - [Ger pods filtered by a label](#ger-pods-filtered-by-a-label)
  - [Watch pod status](#watch-pod-status)
  - [Delete pod](#delete-pod)
  - [Get resource utilisation](#get-resource-utilisation)
  - [View Node port](#view-node-port)
  - [View logs](#view-logs)
  - [Deployments](#deployments)
  - [Port forward into a poc](#port-forward-into-a-poc)
  - [Config maps](#config-maps)
  - [SSH into a pod](#ssh-into-a-pod)
  - [Get service info (including FQDN)](#get-service-info-including-fqdn)
  - [Working with horizontal pod auto-scaler](#working-with-horizontal-pod-auto-scaler)
    - [Get config](#get-config)
    - [Edit config](#edit-config)
- [EKS](#eks)
  - [Create cluster](#create-cluster)
  - [Get clusters](#get-clusters)
  - [Delete cluster](#delete-cluster)
  - [Get nodegroup of a cluster](#get-nodegroup-of-a-cluster)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Docker
## View images
```shell
docker images
```

## Build image from dockerfile
```shell
docker build -t anuragkapur/node-docker-hello-world .
```

## Remove image
```shell
docker rmi anuragkapur/node-web-app
```

## Run an image
```shell
# Default run commad
docker run 678422363581.dkr.ecr.eu-west-2.amazonaws.com/zzish-api:1.7.0

# Run image and map conatiner port to a port on the host machine
# Map conatiner port 3000 to 8080 on host machine
docker run -p 8080:3000 anuragkapur/node-docker-hello-world
```

## Stop a container
```shell
docker stop <containerId>
```

## List containers
```shell
docker container ls
```

## Docker system cleanup
```shell
docker system prune
```

## Login and pull image from AWS ECR
```shell
aws ecr get-login --region eu-west-2 --no-include-email
# Run the command returned in the output of the command above
docker pull 678422363581.dkr.ecr.eu-west-2.amazonaws.com/api:v1.7.1
```   

## Push image to container registry
```shell
docker push anuragkapur/node-docker-hello-world
```

## Copy file from container to localhost
```shell
docker cp <containerId>:/file/path/within/container /host/path/targets
```

## SSH into container
```shell
docker exec -it <containerId> /bin/bash
```

# Kubernetes
[https://kubernetes.io/docs/reference/kubectl/cheatsheet/](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) 

## Get pods and node info
```shell
kubectl get pods -o wide
```

### Ger pods filtered by a label
```shell
kb get nodes --show-labels --selector=kubernetes.io/lifecycle=spot
````

## Watch pod status
```shell
watch -n 1 -x kubectl get pods -n prod
```

## Delete pod
```shell
kb delete pods quizplayer-556bd5d7f8-gxczl
```

## Get resource utilisation
```shell
kubectl top pod
kubectl top node
```

## View Node port
```shell
kubectl describe service --all-namespaces | grep -i nodeport
```

## View logs
```shell
kb logs stag-spitafields-99b8bf696-ffn76 -n stag -f
kb logs -l app=spitafields -n prod -f --max-log-requests=10
``` 
    
## Deployments
```shell
kb get deployments
kb get deployments -n prod
kb edit deployment quizalize
```

## Port forward into a poc
```shell
kb port-forward carmel-9d8d57f75-9qx58 -n stag 3100:3100
```

## Config maps
```shell
kubectl create config stag-spitafields-25apr19v1 --from-env-file=tech-stuff/workspace/zzish/kubernetes/test-environment/spitafields/spitafields.stag.env -n stag
kubectl get configmap stag-spitafields-24august -n stag -o yaml
kubectl get pods -n prod | grep Evicted | awk '{print $1}' | xargs kubectl delete pod -n prod
```

## SSH into a pod
```shell
kb exec -it stag-spitafields-6f755588dc-vrldn sh
```

## Get service info (including FQDN)
```shell
kubectl get service ecsdemo-frontend -o wide
```

## Working with horizontal pod auto-scaler

Ref: https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/

### Get config
```shell
kubectl get hpa
```

### Edit config
```shell
kubectl edit hpa
```

# EKS
## Create cluster
```shell
eksctl create cluster --name ak-eks-playground --version 1.13 --nodegroup-name standard-workers --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --node-ami auto --region eu-central-1
```

## Get clusters
```shell
eksctl get clusters
```

## Delete cluster
```shell
eksctl delete cluster --name ak-eks-playground --region eu-west-1
```

## Get nodegroup of a cluster
```shell
eksctl get nodegroup --cluster ak-eks-playground --region eu-central-1
```

