---
layout: post
title:  "Containers cheat sheet"
teaser: Containers cheat sheet - docker, kubernetes, eks
date:   2019-04-20 00:00:00 +0000
categories: cheat-sheets
tags: cheat-sheets
---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Docker](#docker)
  - [View images](#view-images)
  - [Build image from dockerfile](#build-image-from-dockerfile)
  - [Remove image](#remove-image)
  - [Run an image](#run-an-image)
  - [Docker system cleanup](#docker-system-cleanup)
  - [Login and pull image from AWS ECR](#login-and-pull-image-from-aws-ecr)
  - [Copy file from container to localhost](#copy-file-from-container-to-localhost)
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
```shell script
docker images
```

## Build image from dockerfile
```shell script
docker build -t anuragkapur/node-docker-hello-world .
```

## Remove image
```shell script
docker rmi anuragkapur/node-web-app
```

## Run an image
```shell script
# Default run commad
docker run 678422363581.dkr.ecr.eu-west-2.amazonaws.com/zzish-api:1.7.0

# Run image and map conatiner port to a port on the host machine
# Map conatiner port 3000 to 8080 on host machine
docker run -p 8080:3000 anuragkapur/node-docker-hello-world
```

## Docker system cleanup
```shell script
docker system prune
```

## Login and pull image from AWS ECR
```shell script
aws ecr get-login --region eu-west-2 --no-include-email
# Run the command returned in the output of the command above
docker pull 678422363581.dkr.ecr.eu-west-2.amazonaws.com/api:v1.7.1
```   

## Push image to container registry
```shell script
docker push anuragkapur/node-docker-hello-world
```

## Copy file from container to localhost
```shell script
docker cp <containerId>:/file/path/within/container /host/path/targets
```

# Kubernetes
[https://kubernetes.io/docs/reference/kubectl/cheatsheet/](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) 

## Get pods and node info
```shell script
kubectl get pods -o wide
```

### Ger pods filtered by a label
```shell script
kb get nodes --show-labels --selector=kubernetes.io/lifecycle=spot
````

## Watch pod status
```shell script
watch -n 1 -x kubectl get pods -n prod
```

## Delete pod
```shell script
kb delete pods quizplayer-556bd5d7f8-gxczl
```

## Get resource utilisation
```shell script
kubectl top pod
kubectl top node
```

## View Node port
```shell script
kubectl describe service --all-namespaces | grep -i nodeport
```

## View logs
```shell script
kb logs stag-spitafields-99b8bf696-ffn76 -n stag -f
kb logs -l app=spitafields -n prod -f --max-log-requests=10
``` 
    
## Deployments
```shell script
kb get deployments
kb get deployments -n prod
kb edit deployment quizalize
```

## Port forward into a poc
```shell script
kb port-forward carmel-9d8d57f75-9qx58 -n stag 3100:3100
```

## Config maps
```shell script
kubectl create config stag-spitafields-25apr19v1 --from-env-file=tech-stuff/workspace/zzish/kubernetes/test-environment/spitafields/spitafields.stag.env -n stag
kubectl get configmap stag-spitafields-24august -n stag -o yaml
kubectl get pods -n prod | grep Evicted | awk '{print $1}' | xargs kubectl delete pod -n prod
```

## SSH into a pod
```shell script
kb exec -it stag-spitafields-6f755588dc-vrldn sh
```

## Get service info (including FQDN)
```shell script
kubectl get service ecsdemo-frontend -o wide
```

## Working with horizontal pod auto-scaler

Ref: https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/

### Get config
```shell script
kubectl get hpa
```

### Edit config
```shell script
kubectl edit hpa
```

# EKS
## Create cluster
```shell script
eksctl create cluster --name ak-eks-playground --version 1.13 --nodegroup-name standard-workers --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --node-ami auto --region eu-central-1
```

## Get clusters
```shell script
eksctl get clusters
```

## Delete cluster
```shell script
eksctl delete cluster --name ak-eks-playground --region eu-west-1
```

## Get nodegroup of a cluster
```shell script
eksctl get nodegroup --cluster ak-eks-playground --region eu-central-1
```

